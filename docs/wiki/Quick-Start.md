# Quick Start Guide

Get up and running with GitHub Forge Pipeline in 5 minutes.

## Step 1: Access the Project

1. Go to https://github.com/users/harkers/projects/2
2. Bookmark this page — it's your command center

## Step 2: Create Your First Item

### Option A: Via Issue Template (Recommended)

1. Go to the [repository](https://github.com/harkers/github-forge-pipeline)
2. Click **Issues** → **New issue**
3. Choose a template:
   - **General Work Item** — Any task
   - **Pro Incident** — Privacy incident
   - **Home Task** — Personal task
4. Fill in the form
5. Submit

### Option B: Via GitHub CLI

```bash
# Create a general work item
gh issue create --repo harkers/github-forge-pipeline \
  --template 01-general-work-item.yml

# Create a home task
gh issue create --repo harkers/github-forge-pipeline \
  --template 08-home-task.yml
```

## Step 3: The Item Appears in the Project

New items automatically appear in the project board:
- **Column**: Todo
- **Status**: Inbox (use labels)
- **Fields**: Empty until you set them

## Step 4: Set the Fields

Edit the item in the project board:

1. **GFP Priority** — P0 (urgent) to P4 (scheduled)
2. **Workstream** — ProPharma, HSBC, Home, or Masonic
3. **Initiative** — The appropriate bucket
4. **Task ID** — Format: GFP-PP-INC-001
5. **Due Date** — When it needs to be done
6. **Next Action** — Immediate next step

## Step 5: Track and Update

As work progresses:

1. **Move status** — Todo → In Progress → Done
2. **Update Next Action** — Keep it current
3. **Adjust Priority** — Bump up/down as needed

## Daily Workflow

### Morning
1. Check **P0/P1 Focus** view
2. Update items you're working on
3. Clear any blockers

### Weekly
1. Review **This Week** view
2. Triage Inbox items
3. Update priorities

### Views to Bookmark

| View | When to Use |
|------|-------------|
| P0/P1 Focus | Daily priority check |
| This Week | Weekly planning |
| Waiting | Review stalled work |
| [Your Workstream] | Focused review |

## Naming Quick Reference

### Task ID Format
```
GFP-<WORKSTREAM>-<INITIATIVE>-<NUMBER>

Workstream codes:
- PP = ProPharma
- HB = HSBC
- HM = Home
- MS = Masonic

Examples:
- GFP-PP-INC-001 — ProPharma Incident
- GFP-HM-CAR-002 — Home Career
```

### Issue Title Format
```
[GFP-XX-XXX-NNN] Brief description

Examples:
- [GFP-PP-INC-001] Assess confidentiality incident
- [GFP-HM-CAR-002] Send CV to recruiter
```

## Priority Guide

| Priority | When to Use | Response Time |
|----------|-------------|---------------|
| P0 | Today only | Immediate |
| P1 | This week | Within 24h |
| P2 | This fortnight | Within a few days |
| P3 | Backlog | When capacity allows |
| P4 | Future-dated | Scheduled date |

## Need Help?

- [Full Handbook](https://github.com/harkers/github-forge-pipeline/blob/main/docs/github-forge-pipeline-handbook.md)
- [Implementation Status](https://github.com/harkers/github-forge-pipeline/blob/main/docs/IMPLEMENTATION-STATUS.md)
- Create a [Taxonomy Change Request](https://github.com/harkers/github-forge-pipeline/issues/new?template=11-taxonomy-change.yml)

---

*Last updated: 2026-03-26*
