# GitHub Forge Pipeline

Master planning and tracking for Forge workstreams using GitHub Projects V2.

## Purpose

GitHub Forge Pipeline (GFP) provides a single governed planning and tracking structure for work across four domains:

- **Forge-ProPharma** — Privacy, governance, compliance
- **Forge-HSBC** — Work-specific professional
- **Forge-Home** — Personal, life admin
- **Forge-Masonic** — Masonic duties

## Key Principles

- **One master project** — All work in a single GitHub Project
- **Clear workstream separation** — Distinct domains, shared control plane
- **Stable naming & numbering** — Every item has a GFP-XXX code
- **Priority ≠ Status** — Urgency and workflow are separate controls
- **GitHub as source of truth** — No sync layer, no duplicate systems

## Quick Start

| Task | Command |
|------|---------|
| Create new work item | Use issue template in GitHub |
| View all work | [GitHub Project](https://github.com/users/harkers/projects/2) |
| Filter by workstream | Use Workstream field |
| Filter by priority | Use Priority field |

## Documentation

- [Handbook](docs/github-forge-pipeline-handbook.md) — Complete guide
- [Implementation Plan](docs/GFP-IMPL-001-phased-implementation-plan.md) — Setup steps
- [Design Docs](design/) — UI/UX design specifications

## Taxonomy

### Workstreams

| Code | Workstream |
|------|------------|
| PP | Forge-ProPharma |
| HB | Forge-HSBC |
| HM | Forge-Home |
| MS | Forge-Masonic |

### Status Flow

```
Inbox → Ready → In Progress → Waiting → Blocked → Review → Done
                ↓
            Deferred → Abandoned
```

### Priority

| Code | Definition |
|------|------------|
| P0 | Must complete today |
| P1 | Must complete this week |
| P2 | Should complete this fortnight |
| P3 | Backlog, no deadline |
| P4 | Future-dated, waiting |

### Task ID Format

```
GFP-<WORKSTREAM>-<INITIATIVE>-<NUMBER>

Examples:
- GFP-PP-INC-001 — ProPharma Incident
- GFP-HB-TIA-002 — HSBC Transfer Assessment
- GFP-HM-CAR-003 — Home Career task
```

## Project Structure

```
github-forge-pipeline/
├── docs/                    # Handbook and reference
│   ├── 01-purpose.md
│   ├── 02-scope.md
│   ├── ...
│   └── github-forge-pipeline-handbook.md
├── design/                  # UI/UX design docs
├── .github/
│   └── ISSUE_TEMPLATE/      # Issue templates
│       ├── 01-general-work-item.yml
│       ├── 02-pro-incident.yml
│       └── ...
└── README.md
```

## Issue Templates

| Template | Purpose |
|----------|---------|
| General Work Item | Generic task |
| Pro Incident | Privacy incident (ProPharma) |
| Pro Incident Reporting | Cross-incident reporting |
| Pro Vendor/Subprocessor | Vendor review |
| Pro Assessment | Privacy assessment |
| Pro Data Rights | Data subject rights |
| Pro ROPA | ROPA activity |
| Home Task | Personal task |
| Home Career | Career opportunity |
| Masonic Task | Masonic duty |
| Taxonomy Change | Framework change request |

## Project Views

- **All Work** — Full visibility
- **P0/P1 Focus** — Immediate priorities
- **This Week** — Near-term planning
- **Waiting** — Blocked items
- **Forge-ProPharma** | **Forge-HSBC** | **Forge-Home** | **Forge-Masonic** — By workstream
- **Incidents** | **Vendors** | **Assessments** — By type
- **Done** — Completed work

## Contributing

This is a personal project management framework. Changes require approval via the [Taxonomy Change template](.github/ISSUE_TEMPLATE/11-taxonomy-change.yml).

## License

MIT
