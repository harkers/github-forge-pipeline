# MEMORY.md — GitHub Forge Pipeline

## Project Identity

**Project Code:** GFP-001  
**Master Shorthand:** GFP  
**Name:** GitHub Forge Pipeline — Bidirectional Project Sync  
**Type:** Integration / Synchronization Service  
**Status:** `design`  
**Created:** 2026-03-26

## Purpose

Bidirectional synchronization between GitHub Projects V2 and Forge Pipeline. Enables:

1. GitHub Issues → Forge Pipeline Tasks
2. Forge Pipeline Tasks → GitHub Issues
3. Status field mapping
4. Label/tag mapping
5. Conflict resolution

## Architecture Summary

```
GitHub API ◄──────► Sync Engine ◄──────► Forge Pipeline API
     │                   │                      │
     ▼                   ▼                      ▼
GraphQL          SQLite/Redis State        REST API
Webhooks         Conflict Resolution       Webhooks
```

## Key Documents

| Code | Document | Status |
|------|----------|--------|
| GFP-DOC-001 | Project Definition | Draft |
| GFP-DOC-101 | Domain Architecture | Draft |
| GFP-DOC-201 | Sync Specification | Draft |
| GFP-DOC-301 | Field Mapping | Planned |

## Ownership Rules

| Field | GitHub Wins | Forge Pipeline Wins |
|-------|-------------|-------------------|
| title | ✓ | — |
| description | ✓ | — |
| status | — | ✓ |
| priority | Last-modified | Last-modified |
| tags/labels | Merge | Merge |
| dueDate | — | ✓ |
| riskState | — | ✓ |
| assignees | ✓ | — |

## Implementation Phases

| Phase | Focus | Status |
|-------|-------|--------|
| Phase 1 | Foundation | Not Started |
| Phase 2 | GitHub → Forge Pipeline | Not Started |
| Phase 3 | Bidirectional | Not Started |
| Phase 4 | Hardening | Not Started |

## Technical Decisions

### 2026-03-26: Architecture Decisions

1. **SQLite + Redis for state**: Local state in SQLite, cache in Redis for performance
2. **Webhook-driven sync**: Both GitHub and Forge Pipeline send webhooks for events
3. **GraphQL for GitHub**: GitHub Projects V2 requires GraphQL API
4. **Ownership rules**: Field-level ownership, not entity-level

### 2026-03-26: Conflict Resolution

1. **Conflict window**: 60 seconds for simultaneous modification detection
2. **Resolution order**: Ownership rules → Last-modified → GitHub wins → Manual queue
3. **No auto-delete**: Never automatically delete data on conflict

## Rate Limits

- GitHub API: 5000 requests/hour (authenticated)
- Backoff: Exponential with rate limit header awareness
- Queue: Buffer events during rate limit periods

## Integration Points

| System | Endpoint | Purpose |
|--------|----------|---------|
| GitHub | `/api/github/webhook` | Receive GitHub events |
| Forge Pipeline | `/api/forge-pipeline/webhook` | Receive Forge Pipeline events |
| Forge Pipeline | `/api/projects`, `/api/tasks` | CRUD operations |
| GitHub | GraphQL API | Read/write GitHub Projects |

## Workspace Files

```
github-forge-pipeline/
├── AGENTS.md              # Workspace rules
├── SOUL.md                # Identity
├── USER.md                # Stakeholder context
├── MEMORY.md              # This file
├── memory/                # Daily notes
├── docs/                  # Design docs
│   ├── DFF-CFG-DES-DOC-001-project-definition.md
│   ├── DFF-CFG-DES-DOC-101-domain-architecture.md
│   └── DFF-CFG-DES-DOC-201-sync-specification.md
├── sync/                  # Sync logic (planned)
├── mappings/              # Field mappings (planned)
├── state/                 # Sync state (planned)
└── references/            # External docs (planned)
```

## Next Actions

1. Define field mapping JSON schemas
2. Create sync state database schema
3. Design GitHub GraphQL queries
4. Implement sync engine skeleton

---

*Update this file with significant decisions, state changes, and lessons learned.*