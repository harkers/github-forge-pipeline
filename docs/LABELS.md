# Label Taxonomy

This file documents the complete label taxonomy for GitHub Forge Pipeline.

## Label Count

Total custom labels: **27**

## Categories

### Workstream Labels (4)

| Label | Color | Description |
|-------|-------|-------------|
| `workstream:propharma` | `#0E8A16` (green) | Forge-ProPharma work |
| `workstream:hsbc` | `#1D76DB` (blue) | Forge-HSBC work |
| `workstream:home` | `#D4C5F9` (purple) | Forge-Home work |
| `workstream:masonic` | `#FBCA04` (yellow) | Forge-Masonic work |

### Priority Labels (5)

| Label | Color | Description |
|-------|-------|-------------|
| `priority:urgent` | `#B60205` (red) | P0 - Must complete today |
| `priority:high` | `#D93F0B` (orange) | P1 - Must complete this week |
| `priority:medium` | `#FBCA04` (yellow) | P2 - Should complete this fortnight |
| `priority:low` | `#0E8A16` (green) | P3 - Backlog, no deadline |
| `priority:scheduled` | `#1D76DB` (blue) | P4 - Future-dated, waiting |

### Status Labels (8)

| Label | Color | Description |
|-------|-------|-------------|
| `status:inbox` | `#BFD4F2` (light blue) | Newly captured, untriaged |
| `status:triage` | `#C5DEF5` (lighter blue) | Awaiting classification |
| `status:active` | `#0E8A16` (green) | In progress |
| `status:blocked` | `#B60205` (red) | Blocked on dependency |
| `status:review` | `#D4C5F9` (purple) | Awaiting review |
| `status:done` | `#EDEDED` (gray) | Completed |
| `status:deferred` | `#FBCA04` (yellow) | Deferred |
| `status:abandoned` | `#000000` (black) | Abandoned |

### Type Labels (6)

| Label | Color | Description |
|-------|-------|-------------|
| `type:incident` | `#B60205` (red) | Privacy incident |
| `type:assessment` | `#D4C5F9` (purple) | Privacy assessment |
| `type:vendor` | `#1D76DB` (blue) | Vendor-related |
| `type:ropa` | `#0E8A16` (green) | ROPA activity |
| `type:data-rights` | `#FBCA04` (yellow) | Data rights request |
| `type:task` | `#EDEDED` (gray) | General task |

## Default Labels (9)

These are GitHub's default labels that remain available:

- `bug` — Something isn't working
- `documentation` — Improvements or additions to documentation
- `duplicate` — This issue or pull request already exists
- `enhancement` — New feature or request
- `good first issue` — Good for newcomers
- `help wanted` — Extra attention is needed
- `invalid` — This doesn't seem right
- `question` — Further information is requested
- `wontfix` — This will not be worked on

## Usage

### Creating an Issue with Labels

```bash
gh issue create --title "[GFP-PP-INC-001] Assess confidentiality incident" \
                --body "Incident details..." \
                --label "workstream:propharma,priority:urgent,type:incident,status:active"
```

### Filtering by Labels

```bash
gh issue list --label "priority:urgent"
gh issue list --label "workstream:propharma"
gh issue list --label "status:blocked"
```

## Label Management Commands

### Create a new label
```bash
gh label create "LABEL_NAME" --color HEXCOLOR --description "Description"
```

### Delete a label
```bash
gh label delete "LABEL_NAME"
```

### List all labels
```bash
gh label list
```

---

*Generated: 2026-03-26*
