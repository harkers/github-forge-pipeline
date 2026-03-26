# AGENTS.md — GitHub Forge Pipeline Workspace

This workspace manages **project management using GitHub as the system of record**.

## Purpose

GitHub Forge Pipeline (GFP) provides a single governed planning and tracking structure for work across Forge workstreams:

- **Forge-ProPharma** — Professional, privacy, compliance
- **Forge-HSBC** — Work-specific
- **Forge-Home** — Personal, life admin
- **Forge-Masonic** — Masonic duties

**Key principle:** GitHub Issues and Projects V2 are the master planning layer. No separate database, no sync layer, no duplicate systems.

## Workspace Structure

```
github-forge-pipeline/
├── AGENTS.md              # This file — workspace rules
├── SOUL.md                # Workspace identity
├── USER.md                # Stakeholder context
├── MEMORY.md              # Long-term memory
├── memory/                # Daily session notes
├── para/                  # Durable knowledge
├── docs/                  # Design documentation
├── design/                # UI/UX design docs
├── .github/ISSUE_TEMPLATE/ # GitHub issue templates
├── mappings/              # Field mappings (status, priority, labels)
└── references/            # External reference docs
```

## GitHub Project Structure

### Repository

- **Location:** `github.com/harkers/github-forge-pipeline`
- **Issues:** All tracked work
- **Projects V2:** Master project with custom fields

### Project Fields

| Field | Type | Options |
|-------|------|---------|
| Status | Single select | inbox, triage, active, blocked, review, done, deferred, abandoned |
| Priority | Single select | urgent, high, medium, low, scheduled |
| Workstream | Single select | Forge-ProPharma, Forge-HSBC, Forge-Home, Forge-Masonic |
| Initiative | Single select | Defined per workstream |
| Task ID | Text | GFP-XXX format |
| Due Date | Date | Target completion |
| Risk State | Single select | on-track, at-risk, blocked |

### Labels

Standard labels for filtering and categorization:
- `workstream:propharma`, `workstream:hsbc`, `workstream:home`, `workstream:masonic`
- `priority:urgent`, `priority:high`, `priority:medium`, `priority:low`
- `status:inbox`, `status:triage`, `status:active`, etc.
- `type:incident`, `type:assessment`, `type:vendor`, `type:task`

## Issue Templates

Located in `.github/ISSUE_TEMPLATE/`:

| Template | Purpose |
|----------|---------|
| 01-general-work-item | Generic task |
| 02-pro-incident | Privacy incident |
| 03-pro-incident-reporting | Incident reporting |
| 04-pro-vendor-subprocessor | Vendor/subprocessor |
| 05-pro-assessment | Privacy assessment |
| 06-pro-data-rights | Data rights |
| 07-pro-ropa | ROPA activity |
| 08-home-task | Home task |
| 09-home-career | Career task |
| 10-masonic-task | Masonic task |
| 11-taxonomy-change | Taxonomy update |

## Naming Convention

### Task IDs

Format: `GFP-XXX` where XXX is a sequential number.

Examples:
- `GFP-001` — Project setup
- `GFP-042` — Incident: Wrong recipient email

### Issue Titles

Format: `[WORKSTREAM] Brief description`

Examples:
- `[PRO] Incident: Customer data sent to wrong recipient`
- `[HOME] Schedule annual dental checkup`
- `[MASON] Respond to Lodge meeting invitation`

## Workflow

### Status Flow

```
inbox → triage → active → blocked → review → done
                    ↓
                deferred
                    ↓
                abandoned
```

### Priority Definitions

| Priority | Definition |
|----------|------------|
| urgent | Must complete today |
| high | Must complete this week |
| medium | Should complete this fortnight |
| low | Backlog, no deadline |
| scheduled | Future-dated, waiting |

## Views

Recommended project views:

1. **All Issues** — Everything, sorted by status then priority
2. **By Workstream** — Grouped by workstream field
3. **Active Work** — Status = active or blocked
4. **Urgent/High** — Priority = urgent or high
5. **Incidents** — Label = type:incident

## Forge Pipeline Web App

**Status:** On hold. The Forge Pipeline web app (previously at titan:4174) is no longer active. GitHub Projects V2 is now the sole system of record.

## Self-Improvement

Use the `self-improvement` skill when:
- Taxonomy changes are needed
- Labels or fields need adjustment
- Issue templates need updates
- Workstream definitions change

## Self-Reflection

Use the `self-reflection` skill after:
- Major taxonomy changes
- Template additions/updates
- Workflow adjustments
- Project restructuring

<!-- MEMORY-STACK-HARDENED:START -->
## Memory Stack Rules
- Keep `AGENTS.md` focused on approvals, stop behavior, ownership, and durable operating rules.
- Keep `MEMORY.md` as a tiny routing layer.
- Put durable facts in `para/`.
- Put daily residue in `memory/YYYY-MM-DD.md`.
- If something must survive compaction, promote it into a durable file this session.
- Do not store secrets in memory files.
- Treat QMD as optional additive retrieval, not canonical truth.
<!-- MEMORY-STACK-HARDENED:END -->