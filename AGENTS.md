# AGENTS.md — GitHub Forge Pipeline Workspace

This workspace manages the **bidirectional sync between GitHub Projects V2 and Forge Pipeline**.

## Purpose

GitHub Forge Pipeline (GFP) synchronizes:
- GitHub Issues ↔ Forge Pipeline Tasks
- GitHub Pull Requests ↔ Forge Pipeline Tasks
- GitHub Project V2 status ↔ Forge Pipeline status
- Labels/Tags bidirectionally

## Workspace Structure

```
github-forge-pipeline/
├── AGENTS.md              # This file — workspace rules
├── SOUL.md                # Workspace identity
├── USER.md                # Stakeholder context
├── MEMORY.md              # Long-term memory
├── memory/                # Daily session notes
├── docs/                  # Design documentation
├── sync/                  # Sync engine specifications
├── mappings/              # Field mapping configs
├── state/                 # Sync state (generated)
└── references/            # External reference docs
```

## Sync Ownership Rules

### Field Ownership

| Field | Owner | Rationale |
|-------|-------|-----------|
| `title` | GitHub | GitHub is canonical for content |
| `description/notes` | GitHub | GitHub is canonical for content |
| `status` | Forge Pipeline | Forge Pipeline is operational source |
| `priority` | Last-modified | Both systems have equal claim |
| `tags/labels` | Merge | Union of both sets |
| `dueDate` | Forge Pipeline | GitHub doesn't have due dates |
| `riskState` | Forge Pipeline | GitHub doesn't have risk state |
| `assignees` | GitHub | GitHub manages assignment |

### Conflict Resolution Order

1. **Check field ownership** — If one system owns the field, that value wins
2. **Check last-modified timestamp** — Most recent change wins
3. **GitHub wins for content** — Default to GitHub for title/description
4. **Manual resolution queue** — Escalate if still unresolved

## Sync Flow

### GitHub → Forge Pipeline

1. Webhook received at `/api/github/webhook`
2. Validate signature
3. Parse event type
4. Lookup sync state
5. Apply ownership rules
6. Update Forge Pipeline via API
7. Update sync state

### Forge Pipeline → GitHub

1. Webhook received at `/api/forge-pipeline/webhook`
2. Validate API key
3. Parse event type
4. Lookup sync state
5. Apply ownership rules
6. Update GitHub via GraphQL API
7. Update sync state

## Rate Limits

- **GitHub API**: 5000 requests/hour
- Implement exponential backoff on rate limit
- Queue events during rate limit periods
- Monitor `X-RateLimit-Remaining` header

## Conflict Handling

When a conflict is detected:

1. Log to `sync_conflicts` table
2. Check ownership rules (which field, which system wins)
3. If unresolved, queue for manual resolution
4. Notify workspace via `MEMORY.md` entry

## Webhook Configuration

### GitHub Webhook

```
URL: {GFP_BASE_URL}/api/github/webhook
Content-Type: application/json
Secret: {GITHUB_WEBHOOK_SECRET}
Events: issues, pull_request, projects_v2_item
```

### Forge Pipeline Webhook

```
URL: {GFP_BASE_URL}/api/forge-pipeline/webhook
Content-Type: application/json
Header: X-API-Key: {FORGE_PIPELINE_API_KEY}
Events: task.created, task.updated, task.deleted, project.updated
```

## MCP Integration

Forge Pipeline can trigger sync via MCP endpoints:

```json
POST /api/gfp/sync/github/{owner}/{repo}
POST /api/gfp/sync/forge-pipeline/{projectId}
```

## State Tracking

All sync state is tracked in `state/sync-state.json`:

```json
{
  "last_sync": "2026-03-26T10:00:00Z",
  "github_rate_remaining": 4987,
  "pending_conflicts": 0,
  "sync_errors": []
}
```

## Forge Pipeline Integration

This workspace registers in Forge Pipeline as:

- **Project ID**: `github-forge-pipeline`
- **Source Tag**: `source:github-forge-pipeline`
- **Sync Tasks**: Created in this workspace's project

## Self-Improvement

Use the `self-improvement` skill when:
- Sync conflicts exceed 5% rate
- GitHub API errors occur unexpectedly
- Field mappings need adjustment
- Rate limits are hit repeatedly

## Self-Reflection

Use the `self-reflection` skill after:
- Major sync incidents
- Manual conflict resolutions
- Field mapping changes
- Architecture updates