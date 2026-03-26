# DFF-CFG-DES-DOC-101 — GitHub Forge Pipeline Architecture

**Code:** DFF-CFG-DES-DOC-101  
**Type:** Document  
**Status:** Draft  
**Created:** 2026-03-26  
**Work Package:** DFF-CFG-DES-WP-003

---

## System Overview

GitHub Forge Pipeline (GFP) is a **bidirectional sync service** that bridges GitHub Projects V2 and Forge Pipeline.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        GITHUB FORGE PIPELINE                                 │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌──────────────────┐     ┌──────────────────┐     ┌──────────────────┐    │
│  │   GitHub API     │     │   Sync Engine    │     │  Forge Pipeline  │    │
│  │   Client         │◄───►│   (Core)          │◄───►│   API            │    │
│  │                  │     │                  │     │                  │    │
│  │  - Projects V2   │     │  - Event Queue   │     │  - Projects     │    │
│  │  - Issues        │     │  - Conflict Res   │     │  - Tasks        │    │
│  │  - Pull Requests │     │  - Field Mapping  │     │  - Events       │    │
│  └──────────────────┘     └──────────────────┘     └──────────────────┘    │
│         │                         │                       │                │
│         ▼                         ▼                       ▼                │
│  ┌──────────────────┐     ┌──────────────────┐     ┌──────────────────┐    │
│  │   GitHub GraphQL │     │   SQLite/Redis   │     │   Forge Pipeline │    │
│  │   API            │     │   State Store    │     │   Database       │    │
│  └──────────────────┘     └──────────────────┘     └──────────────────┘    │
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │                        OPENCLAW WORKSPACE                             │   │
│  │                                                                        │   │
│  │   github-forge-pipeline/                                              │   │
│  │   ├── AGENTS.md          # Workspace rules                            │   │
│  │   ├── docs/              # Documentation                              │   │
│  │   ├── sync/              # Sync logic                                 │   │
│  │   ├── mappings/          # Field mappings                             │   │
│  │   ├── state/             # Sync state                                 │   │
│  │   └── memory/            # Session notes                               │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Components

### 1. GitHub API Client

**Purpose:** Authenticate and communicate with GitHub GraphQL API.

**Responsibilities:**
- OAuth authentication (GitHub App or PAT)
- GraphQL query execution
- Rate limit handling and backoff
- Webhook event reception

**Configuration:**
```yaml
github:
  auth:
    type: github_app  # or personal_access_token
    app_id: ${GITHUB_APP_ID}
    private_key: ${GITHUB_PRIVATE_KEY}
    # OR
    pat: ${GITHUB_PAT}
  
  rate_limit:
    requests_per_hour: 5000
    backoff_strategy: exponential
    max_retries: 3
  
  webhooks:
    secret: ${GITHUB_WEBHOOK_SECRET}
    endpoint: /api/github/webhook
```

---

### 2. Sync Engine (Core)

**Purpose:** Orchestrate bidirectional synchronization.

**Components:**

| Component | Responsibility |
|-----------|---------------|
| **Event Queue** | Buffer incoming events for processing |
| **Conflict Resolver** | Detect and resolve sync conflicts |
| **Field Mapper** | Transform between GitHub and Forge Pipeline schemas |
| **State Tracker** | Track sync state and last sync timestamps |
| **Ownership Manager** | Enforce ownership rules |

**Event Flow:**
```
GitHub Event → Webhook → Event Queue → Conflict Check → Apply → State Update
                                    ↓
                            Conflict Detected?
                                    ↓
                         ┌─────────┴─────────┐
                         │                   │
                    Auto Resolve      Manual Queue
                         │                   │
                         ▼                   ▼
                      Apply Sync      Alert Workspace
```

---

### 3. Forge Pipeline API Client

**Purpose:** Communicate with Forge Pipeline REST API.

**Responsibilities:**
- Project/task CRUD operations
- Event emission for audit trail
- MCP endpoint integration
- Webhook endpoint for Forge Pipeline events

**Configuration:**
```yaml
forge_pipeline:
  api_url: ${FORGE_PIPELINE_URL:-http://localhost:4181}
  api_key: ${FORGE_PIPELINE_API_KEY}
  
  webhooks:
    endpoint: /api/forge-pipeline/webhook
    events:
      - project.created
      - project.updated
      - task.created
      - task.updated
      - task.deleted
```

---

### 4. State Store

**Purpose:** Persist sync state and conflict records.

**Schema:**
```sql
-- Sync state for each entity
CREATE TABLE sync_state (
  id TEXT PRIMARY KEY,
  entity_type TEXT NOT NULL,  -- 'project' | 'task'
  github_id TEXT,              -- GitHub node ID
  forge_pipeline_id TEXT,      -- Forge Pipeline ID
  last_sync_at TEXT NOT NULL,
  last_modified_by TEXT NOT NULL,  -- 'github' | 'forge-pipeline'
  sync_version INTEGER NOT NULL DEFAULT 1,
  conflict_status TEXT DEFAULT 'none',  -- 'none' | 'detected' | 'resolved'
  metadata_json TEXT,
  created_at TEXT NOT NULL,
  updated_at TEXT NOT NULL
);

-- Sync event log
CREATE TABLE sync_events (
  id TEXT PRIMARY KEY,
  source TEXT NOT NULL,        -- 'github' | 'forge-pipeline'
  entity_type TEXT NOT NULL,
  entity_id TEXT NOT NULL,
  action TEXT NOT NULL,        -- 'create' | 'update' | 'delete'
  payload_json TEXT NOT NULL,
  processed_at TEXT,
  status TEXT DEFAULT 'pending',  -- 'pending' | 'processed' | 'failed' | 'conflict'
  error_message TEXT,
  created_at TEXT NOT NULL
);

-- Conflict resolution queue
CREATE TABLE sync_conflicts (
  id TEXT PRIMARY KEY,
  sync_event_id TEXT NOT NULL,
  entity_type TEXT NOT NULL,
  github_state_json TEXT NOT NULL,
  forge_pipeline_state_json TEXT NOT NULL,
  resolution_strategy TEXT,     -- 'github_wins' | 'forge_wins' | 'merge' | 'manual'
  resolved_at TEXT,
  resolved_by TEXT,            -- agent or user
  created_at TEXT NOT NULL
);
```

---

## Ownership Rules

### Conflict Resolution Priority

| Scenario | Resolution | Rationale |
|----------|------------|-----------|
| GitHub issue created | GitHub → Forge Pipeline | New content flows from GitHub |
| Forge Pipeline task created | Forge Pipeline → GitHub | New content flows to GitHub |
| Both modified simultaneously | Last-modified wins | Most recent change preserved |
| Field conflict (status) | Forge Pipeline wins | Forge Pipeline is operational source |
| Field conflict (description) | GitHub wins | GitHub is canonical for content |
| Delete conflict | Manual resolution | Prevents data loss |

### Field Ownership Matrix

| Field | GitHub Owner | Forge Pipeline Owner | Notes |
|-------|--------------|---------------------|-------|
| `title` | ✓ | ✗ | GitHub canonical |
| `description/notes` | ✓ | ✗ | GitHub canonical |
| `status` | ✗ | ✓ | Forge Pipeline operational |
| `priority` | ✓ | ✓ | Bidirectional |
| `labels/tags` | ✓ | ✓ | Mapped bidirectionally |
| `assignees` | ✓ | ✗ | GitHub canonical |
| `due_date` | ✗ | ✓ | Forge Pipeline canonical |
| `risk_state` | ✗ | ✓ | Forge Pipeline only |
| `project` | ✓ | ✗ | GitHub Project assignment |

---

## Sync Events

### GitHub → Forge Pipeline

| Event | Action |
|-------|--------|
| `issues.opened` | Create Forge Pipeline task |
| `issues.closed` | Set task status to `done` |
| `issues.reopened` | Set task status to `todo` or `in-progress` |
| `issues.edited` | Update task title/description |
| `issues.labeled` | Add tags to task |
| `issues.unlabeled` | Remove tags from task |
| `issues.assigned` | Update task metadata |
| `pull_request.opened` | Create task with PR type |
| `pull_request.closed` | Update task status (merged → done, closed → cancelled) |
| `pull_request.ready_for_review` | Update task status |

### Forge Pipeline → GitHub

| Event | Action |
|-------|--------|
| `task.created` | Create GitHub issue |
| `task.updated.status` | Add label or close issue |
| `task.updated.priority` | Add priority label |
| `task.updated.dueDate` | Add milestone (if mapped) |
| `task.deleted` | Close issue with comment |

---

## API Endpoints

### Sync Management

| Endpoint | Method | Purpose |
|----------|--------|---------|
| `/api/gfp/status` | GET | Sync service status |
| `/api/gfp/sync/github/{owner}/{repo}` | POST | Trigger manual GitHub sync |
| `/api/gfp/sync/forge-pipeline/{projectId}` | POST | Trigger manual Forge Pipeline sync |
| `/api/gfp/conflicts` | GET | List pending conflicts |
| `/api/gfp/conflicts/{id}/resolve` | POST | Resolve conflict manually |
| `/api/gfp/mappings` | GET | List field mappings |
| `/api/gfp/mappings` | PUT | Update field mappings |

### Webhooks

| Endpoint | Method | Purpose |
|----------|--------|---------|
| `/api/github/webhook` | POST | Receive GitHub webhooks |
| `/api/forge-pipeline/webhook` | POST | Receive Forge Pipeline webhooks |

---

## OpenClaw Workspace

### Directory Structure

```
github-forge-pipeline/
├── AGENTS.md                    # Workspace rules (GFP-specific)
├── SOUL.md                      # Workspace identity
├── USER.md                      # Stakeholder context
├── MEMORY.md                    # Long-term memory
├── memory/                      # Daily session notes
│   └── 2026-03-26.md
├── docs/
│   ├── DFF-CFG-DES-DOC-001-project-definition.md
│   ├── DFF-CFG-DES-DOC-101-domain-architecture.md
│   ├── DFF-CFG-DES-DOC-201-sync-specification.md
│   └── DFF-CFG-DES-DOC-301-field-mapping.md
├── sync/
│   ├── github-client.md         # GitHub API client spec
│   ├── forge-client.md          # Forge Pipeline client spec
│   ├── engine.md                # Sync engine logic
│   └── conflict.md              # Conflict resolution rules
├── mappings/
│   ├── status-mapping.json      # Status field mapping
│   ├── priority-mapping.json    # Priority field mapping
│   └── label-mapping.json       # Label/tag mapping
├── state/
│   ├── sync-state.json          # Current sync state (generated)
│   └── config.yaml              # GFP configuration
└── references/
    ├── github-graphql-schema.md # GitHub GraphQL reference
    └── forge-pipeline-api.md    # Forge Pipeline API reference
```

### AGENTS.md Rules

```markdown
# AGENTS.md — GitHub Forge Pipeline Workspace

## Workspace Purpose

This workspace manages the bidirectional sync between GitHub Projects V2 
and Forge Pipeline. All sync operations, conflict resolution, and mapping 
configuration happen here.

## Sync Ownership Rules

1. GitHub is canonical for: title, description, assignees, labels
2. Forge Pipeline is canonical for: status (operational), due_date, risk_state
3. Bidirectional sync: priority, tags/labels

## Conflict Resolution

When a conflict is detected:
1. Check ownership rules (which field, which system wins)
2. If ownership is unclear, check last-modified timestamp
3. If still unclear, queue for manual resolution
4. Manual resolution requires agent or user action

## Webhook Handling

- GitHub webhooks → `/api/github/webhook`
- Forge Pipeline webhooks → `/api/forge-pipeline/webhook`
- All events logged to sync_events table
- Conflicts logged to sync_conflicts table

## Rate Limits

- Respect GitHub API rate limits (5000 requests/hour)
- Implement exponential backoff on rate limit
- Queue events during rate limit periods
```

---

## Implementation Phases

### Phase 1: Foundation (Week 1)
- [ ] OpenClaw workspace setup
- [ ] GitHub API client implementation
- [ ] Forge Pipeline API client implementation
- [ ] State store schema
- [ ] Basic sync engine skeleton

### Phase 2: Unidirectional Sync (Week 2)
- [ ] GitHub → Forge Pipeline sync
- [ ] Event handling (issues, PRs)
- [ ] Field mapping (basic)
- [ ] State tracking

### Phase 3: Bidirectional Sync (Week 3)
- [ ] Forge Pipeline → GitHub sync
- [ ] Conflict detection
- [ ] Ownership rule enforcement
- [ ] Manual conflict resolution

### Phase 4: Hardening (Week 4)
- [ ] Rate limit handling
- [ ] Error recovery
- [ ] Audit logging
- [ ] Testing suite

---

## References

- DFF-CFG-DES-DOC-001 — Project Definition
- DFF-CFG-DES-DOC-201 — Sync Specification
- DFF-CFG-DES-DOC-301 — Field Mapping
- GitHub Projects V2 API Documentation
- Forge Pipeline API Specification

---

*This document defines the domain architecture for GitHub Forge Pipeline.*