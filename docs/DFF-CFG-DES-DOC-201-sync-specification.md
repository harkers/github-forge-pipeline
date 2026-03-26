# DFF-CFG-DES-DOC-201 — Sync Specification

**Code:** DFF-CFG-DES-DOC-201  
**Type:** Document  
**Status:** Draft  
**Created:** 2026-03-26  
**Work Package:** DFF-CFG-DES-WP-006

---

## Sync Specification Overview

This document defines the detailed synchronization rules, field mappings, and event flows for GitHub Forge Pipeline.

---

## Field Mapping Tables

### Project Mapping

| GitHub Field | Forge Pipeline Field | Direction | Transform |
|--------------|---------------------|-----------|-----------|
| `title` | `name` | Bidirectional | Direct map |
| `body` | `description` | GitHub → Forge Pipeline | Direct map |
| `number` | `metadata.github_number` | GitHub → Forge Pipeline | Store as metadata |
| `id` (node ID) | `metadata.github_node_id` | GitHub → Forge Pipeline | Store as metadata |
| `state` | — | GitHub → Forge Pipeline | Map to status (see Status Mapping) |
| `labels` | `tags` | Bidirectional | Map via label-mapping.json |
| `assignees` | — | GitHub → Forge Pipeline | Store as metadata |
| `milestone` | — | GitHub → Forge Pipeline | Store as metadata |
| `projectItems` | — | GitHub → Forge Pipeline | Link to GitHub Project V2 |
| — | `status` | Forge Pipeline → GitHub | Map to project status field |
| — | `notes` | Forge Pipeline only | Internal context |
| — | `dueDate` | Forge Pipeline only | Not in GitHub Issues |
| — | `riskState` | Forge Pipeline only | Not in GitHub Issues |
| — | `priority` | Bidirectional | Map via priority-mapping.json |

### Task Mapping

| GitHub Field | Forge Pipeline Field | Direction | Transform |
|--------------|---------------------|-----------|-----------|
| `title` | `title` | Bidirectional | Direct map |
| `body` | `notes` | GitHub → Forge Pipeline | Direct map |
| `number` | `metadata.github_number` | GitHub → Forge Pipeline | Store as metadata |
| `id` (node ID) | `metadata.github_node_id` | GitHub → Forge Pipeline | Store as metadata |
| `state` | `status` | Bidirectional | Map via status-mapping.json |
| `labels` | `tags` | Bidirectional | Map via label-mapping.json |
| `assignees.login` | `metadata.assignees` | GitHub → Forge Pipeline | Store as array |
| `milestone.title` | `metadata.milestone` | GitHub → Forge Pipeline | Store as metadata |
| `createdAt` | `metadata.github_created_at` | GitHub → Forge Pipeline | Store as metadata |
| `updatedAt` | `updatedAt` | Bidirectional | Use for conflict detection |
| — | `priority` | Bidirectional | Map via priority-mapping.json |
| — | `dueDate` | Forge Pipeline only | Not in GitHub Issues |
| — | `riskState` | Forge Pipeline only | Not in GitHub Issues |
| — | `blockedBy` | Forge Pipeline only | Internal dependency |
| — | `blocking` | Forge Pipeline only | Internal dependency |

---

## Status Mapping

### GitHub Issue State → Forge Pipeline Task Status

| GitHub `state` | GitHub `stateReason` | Forge Pipeline `status` |
|----------------|---------------------|------------------------|
| `OPEN` | — | `todo` or `in-progress` |
| `CLOSED` | `COMPLETED` | `done` |
| `CLOSED` | `NOT_PLANNED` | `cancelled` |
| `CLOSED` | `REOPENED` | `todo` |
| `CLOSED` | `DUPLICATE` | `cancelled` (with metadata) |

### Forge Pipeline Task Status → GitHub Issue State

| Forge Pipeline `status` | GitHub `state` | GitHub `stateReason` | Notes |
|------------------------|----------------|---------------------|-------|
| `todo` | `OPEN` | — | Default |
| `in-progress` | `OPEN` | — | Add `in-progress` label |
| `blocked` | `OPEN` | — | Add `blocked` label |
| `done` | `CLOSED` | `COMPLETED` | Close issue |
| `cancelled` | `CLOSED` | `NOT_PLANNED` | Close issue |

### GitHub Project V2 Status Field → Forge Pipeline

| GitHub Project Status | Forge Pipeline `status` |
|-----------------------|------------------------|
| `Todo` | `todo` |
| `In Progress` | `in-progress` |
| `In Review` | `in-progress` |
| `Done` | `done` |
| `Cancelled` | `cancelled` |
| `Blocked` | `blocked` |

---

## Priority Mapping

### GitHub Labels → Forge Pipeline Priority

| GitHub Label | Forge Pipeline `priority` |
|--------------|--------------------------|
| `priority: critical` | `critical` |
| `priority: high` | `high` |
| `priority: medium` | `medium` |
| `priority: low` | `low` |
| `P0` | `critical` |
| `P1` | `high` |
| `P2` | `medium` |
| `P3` | `low` |

### Forge Pipeline Priority → GitHub Labels

| Forge Pipeline `priority` | GitHub Label |
|---------------------------|--------------|
| `critical` | `priority: critical` |
| `high` | `priority: high` |
| `medium` | `priority: medium` |
| `low` | `priority: low` |

---

## Label Mapping

### Standard Label Mappings

| GitHub Label | Forge Pipeline Tag | Notes |
|--------------|-------------------|-------|
| `bug` | `bug` | Direct |
| `enhancement` | `enhancement` | Direct |
| `documentation` | `docs` | Remap |
| `good first issue` | `good-first-issue` | Normalize |
| `help wanted` | `help-wanted` | Normalize |
| `question` | `question` | Direct |
| `wontfix` | `wontfix` | Direct |
| `source:*` | `source:*` | Preserve source tag |
| `project:*` | — | Project context only |

### Custom Label Mapping

Custom label mappings are defined in `mappings/label-mapping.json`:

```json
{
  "github_to_forge": {
    "type: bug": "bug",
    "type: enhancement": "enhancement",
    "type: documentation": "docs",
    "priority: critical": "priority:critical",
    "priority: high": "priority:high",
    "priority: medium": "priority:medium",
    "priority: low": "priority:low",
    "status: blocked": "status:blocked",
    "status: in-progress": "status:in-progress"
  },
  "forge_to_github": {
    "bug": "type: bug",
    "enhancement": "type: enhancement",
    "docs": "type: documentation",
    "priority:critical": "priority: critical",
    "priority:high": "priority: high",
    "priority:medium": "priority: medium",
    "priority:low": "priority: low",
    "status:blocked": "status: blocked",
    "status:in-progress": "status: in-progress"
  },
  "preserve_prefix": ["source:"],
  "ignore_labels": ["stale", "wip"]
}
```

---

## Event Processing

### GitHub Webhook Events

| Event | Action | Sync Priority |
|-------|--------|----------------|
| `issues.opened` | Create task | High |
| `issues.closed` | Update status | High |
| `issues.reopened` | Update status | High |
| `issues.edited` | Update title/notes | Medium |
| `issues.labeled` | Update tags | Medium |
| `issues.unlabeled` | Update tags | Medium |
| `issues.assigned` | Update metadata | Low |
| `pull_request.opened` | Create task | High |
| `pull_request.closed` | Update status | High |
| `pull_request.ready_for_review` | Update status | Medium |
| `pull_request.review_requested` | Update metadata | Low |
| `projects_v2_item.created` | Create task | High |
| `projects_v2_item.edited` | Update task | Medium |
| `projects_v2_item.deleted` | Delete task | High |

### Forge Pipeline Webhook Events

| Event | Action | Sync Priority |
|-------|--------|----------------|
| `task.created` | Create GitHub issue | High |
| `task.updated.status` | Update GitHub status | High |
| `task.updated.priority` | Update GitHub labels | Medium |
| `task.updated.tags` | Update GitHub labels | Medium |
| `task.deleted` | Close GitHub issue | High |
| `project.updated` | Sync project metadata | Low |

---

## Sync Flow

### GitHub → Forge Pipeline Flow

```
1. GitHub Webhook Received
   ↓
2. Validate Signature
   ↓
3. Parse Event
   ↓
4. Lookup Sync State
   ├─ Found → Check last_sync_at
   └─ Not Found → Create new sync_state
   ↓
5. Conflict Detection
   ├─ No conflict → Apply sync
   │    ↓
   │  Update Forge Pipeline via API
   │    ↓
   │  Update sync_state (last_sync_at, last_modified_by = 'github')
   │
   └─ Conflict detected → Check ownership rules
        ├─ GitHub wins → Apply sync
        │    ↓
        │  Update Forge Pipeline
        │    ↓
        │  Update sync_state
        │
        └─ Forge Pipeline wins → Skip (no action)
             ↓
           Log conflict (manual resolution queue)
```

### Forge Pipeline → GitHub Flow

```
1. Forge Pipeline Webhook Received
   ↓
2. Validate API Key (if configured)
   ↓
3. Parse Event
   ↓
4. Lookup Sync State
   ├─ Found → Check last_sync_at
   └─ Not Found → Create new sync_state
   ↓
5. Conflict Detection
   ├─ No conflict → Apply sync
   │    ↓
   │  Update GitHub via GraphQL API
   │    ↓
   │  Update sync_state (last_sync_at, last_modified_by = 'forge-pipeline')
   │
   └─ Conflict detected → Check ownership rules
        ├─ Forge Pipeline wins → Apply sync
        │    ↓
        │  Update GitHub
        │    ↓
        │  Update sync_state
        │
        └─ GitHub wins → Skip (no action)
             ↓
           Log conflict (manual resolution queue)
```

---

## Conflict Detection

### Conflict Conditions

A conflict is detected when:

1. **Simultaneous modification**: Both systems modified the same entity within the conflict window (default: 60 seconds)
2. **Field mismatch**: The same field has different values in both systems
3. **Delete vs update**: One system deleted while the other updated

### Conflict Resolution Matrix

| Field Conflict | Resolution | Rationale |
|----------------|------------|-----------|
| `title` | GitHub wins | GitHub is canonical for content |
| `description/notes` | GitHub wins | GitHub is canonical for content |
| `status` | Forge Pipeline wins | Forge Pipeline is operational source |
| `priority` | Last-modified wins | Both systems have equal claim |
| `tags/labels` | Merge | Union of both sets |
| `dueDate` | Forge Pipeline wins | GitHub doesn't have due dates on issues |
| `riskState` | Forge Pipeline wins | GitHub doesn't have risk state |
| `assignees` | GitHub wins | GitHub manages assignment |

### Conflict Window

```yaml
conflict:
  window_seconds: 60
  resolution_order:
    - ownership_rules      # Check field ownership first
    - last_modified_wins   # Use most recent timestamp
    - github_wins          # Default to GitHub for content
    - manual_queue         # Escalate if unresolved
```

---

## Rate Limiting

### GitHub API Rate Limits

| Limit | Value | Handling |
|-------|-------|----------|
| Primary rate limit | 5000 requests/hour | Monitor remaining, queue when low |
| Secondary rate limit | Dynamic | Exponential backoff |
| GraphQL complexity | 50000 points/query | Batch queries, use pagination |

### Backoff Strategy

```python
async def github_request_with_backoff(request_fn, max_retries=3):
    for attempt in range(max_retries):
        response = await request_fn()
        
        if response.status == 200:
            return response
        
        if response.status == 403:  # Rate limited
            reset_time = response.headers.get('X-RateLimit-Reset')
            if reset_time:
                wait_seconds = int(reset_time) - time.time()
                await asyncio.sleep(max(wait_seconds, 1))
            else:
                await asyncio.sleep(2 ** attempt)  # Exponential backoff
        
        elif response.status >= 500:  # Server error
            await asyncio.sleep(2 ** attempt)
    
    raise MaxRetriesExceeded()
```

---

## Sync State Schema

### sync_state Table

```sql
CREATE TABLE sync_state (
  id TEXT PRIMARY KEY,
  entity_type TEXT NOT NULL CHECK (entity_type IN ('project', 'task')),
  github_id TEXT,                    -- GitHub GraphQL node ID
  github_number INTEGER,             -- Issue/PR number
  forge_pipeline_id TEXT NOT NULL,   -- Forge Pipeline ID
  github_url TEXT,                   -- https://github.com/owner/repo/issues/123
  last_sync_at TEXT NOT NULL,        -- ISO timestamp
  last_modified_by TEXT NOT NULL CHECK (last_modified_by IN ('github', 'forge-pipeline')),
  last_modified_at TEXT NOT NULL,    -- ISO timestamp from source
  sync_version INTEGER NOT NULL DEFAULT 1,
  conflict_status TEXT DEFAULT 'none' CHECK (conflict_status IN ('none', 'detected', 'resolving', 'resolved')),
  conflict_id TEXT,                  -- Reference to sync_conflicts
  metadata_json TEXT,                -- Additional metadata
  created_at TEXT NOT NULL,
  updated_at TEXT NOT NULL,
  
  UNIQUE(github_id),
  UNIQUE(forge_pipeline_id)
);

CREATE INDEX idx_sync_state_github_id ON sync_state(github_id);
CREATE INDEX idx_sync_state_forge_id ON sync_state(forge_pipeline_id);
CREATE INDEX idx_sync_state_last_sync ON sync_state(last_sync_at);
CREATE INDEX idx_sync_state_conflict ON sync_state(conflict_status);
```

---

## Webhook Signature Validation

### GitHub Webhook Signature

```python
def validate_github_signature(payload: bytes, signature: str, secret: str) -> bool:
    """Validate GitHub webhook signature using HMAC-SHA256."""
    expected = 'sha256=' + hmac.new(
        secret.encode(),
        payload,
        hashlib.sha256
    ).hexdigest()
    return hmac.compare_digest(signature, expected)
```

### Forge Pipeline API Key

```python
def validate_forge_pipeline_key(api_key: str, expected: str) -> bool:
    """Validate Forge Pipeline API key."""
    if not expected:
        return True  # No key configured, allow all
    return hmac.compare_digest(api_key, expected)
```

---

## References

- DFF-CFG-DES-DOC-001 — Project Definition
- DFF-CFG-DES-DOC-101 — Domain Architecture
- GitHub GraphQL API Documentation
- Forge Pipeline API Specification

---

*This document defines the sync specification for GitHub Forge Pipeline.*