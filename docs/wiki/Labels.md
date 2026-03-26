# Label Reference

Complete reference for all labels in GitHub Forge Pipeline.

## Label Count

Total custom labels: **27**

## Workstream Labels (4)

| Label | Color | Hex | Use For |
|-------|-------|-----|---------|
| `workstream:propharma` | Green | `#0E8A16` | ProPharma work |
| `workstream:hsbc` | Blue | `#1D76DB` | HSBC work |
| `workstream:home` | Purple | `#D4C5F9` | Home/personal work |
| `workstream:masonic` | Yellow | `#FBCA04` | Masonic work |

## Priority Labels (5)

| Label | Color | Hex | Code | Definition |
|-------|-------|-----|------|------------|
| `priority:urgent` | Red | `#B60205` | P0 | Must complete today |
| `priority:high` | Orange | `#D93F0B` | P1 | Must complete this week |
| `priority:medium` | Yellow | `#FBCA04` | P2 | Should complete this fortnight |
| `priority:low` | Green | `#0E8A16` | P3 | Backlog, no deadline |
| `priority:scheduled` | Blue | `#1D76DB` | P4 | Future-dated, waiting |

## Status Labels (8)

| Label | Color | Hex | Definition |
|-------|-------|-----|------------|
| `status:inbox` | Light Blue | `#BFD4F2` | Newly captured, untriaged |
| `status:triage` | Lighter Blue | `#C5DEF5` | Awaiting classification |
| `status:active` | Green | `#0E8A16` | In progress |
| `status:blocked` | Red | `#B60205` | Blocked on dependency |
| `status:review` | Purple | `#D4C5F9` | Awaiting review |
| `status:done` | Gray | `#EDEDED` | Completed |
| `status:deferred` | Yellow | `#FBCA04` | Deferred |
| `status:abandoned` | Black | `#000000` | Abandoned |

## Type Labels (6)

| Label | Color | Hex | Use For |
|-------|-------|-----|---------|
| `type:incident` | Red | `#B60205` | Privacy incidents |
| `type:assessment` | Purple | `#D4C5F9` | Privacy assessments |
| `type:vendor` | Blue | `#1D76DB` | Vendor-related work |
| `type:ropa` | Green | `#0E8A16` | ROPA activities |
| `type:data-rights` | Yellow | `#FBCA04` | Data subject rights |
| `type:task` | Gray | `#EDEDED` | General tasks |

## Default Labels (9)

GitHub's default labels remain available:

- `bug` — Something isn't working
- `documentation` — Documentation improvements
- `duplicate` — Duplicate issue/PR
- `enhancement` — New feature request
- `good first issue` — Good for newcomers
- `help wanted` — Extra attention needed
- `invalid` — Doesn't seem right
- `question` — Further information requested
- `wontfix` — Will not be worked on

## Using Labels

### In Issue Templates

Templates automatically apply appropriate labels:
- `needs-triage` — Initial label for new items
- `workstream:home` — For Home tasks
- `initiative:incidents` — For incident work

### Filtering by Label

**GitHub Web:**
- Go to Issues → Labels
- Click a label to filter

**GitHub CLI:**
```bash
# List issues by label
gh issue list --repo harkers/github-forge-pipeline --label "priority:urgent"

# Multiple labels
gh issue list --label "workstream:propharma,priority:high"

# View project by label
gh project view --owner harkers --number 2
```

### Label Combinations

Common combinations:

| Work Type | Labels |
|-----------|--------|
| Urgent Pro incident | `workstream:propharma`, `priority:urgent`, `type:incident`, `status:active` |
| Home maintenance | `workstream:home`, `priority:medium`, `type:task` |
| Blocked assessment | `priority:high`, `type:assessment`, `status:blocked` |

## Creating New Labels

Only create new labels if approved via taxonomy change process:

```bash
gh label create "new-label" --color HEXCOLOR --description "Description"
```

## Label Maintenance

- **Don't delete** labels in active use
- **Don't rename** without updating all issues
- **Use consistently** — same label, same meaning

---

*Last updated: 2026-03-26*
