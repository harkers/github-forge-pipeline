# GitHub Forge Pipeline Wiki

Welcome to the GitHub Forge Pipeline wiki — quick reference for the project management framework.

## What is GitHub Forge Pipeline?

A single governed planning and tracking structure for work across four domains:

- **Forge-ProPharma** — Privacy, governance, compliance
- **Forge-HSBC** — Work-specific professional
- **Forge-Home** — Personal, life admin
- **Forge-Masonic** — Masonic duties

## Quick Links

- [Project Board](https://github.com/users/harkers/projects/2)
- [Repository](https://github.com/harkers/github-forge-pipeline)
- [Handbook](https://github.com/harkers/github-forge-pipeline/blob/main/docs/github-forge-pipeline-handbook.md)
- [Implementation Status](https://github.com/harkers/github-forge-pipeline/blob/main/docs/IMPLEMENTATION-STATUS.md)

## Creating Work Items

Use the issue templates when creating new items:

| Template | When to Use |
|----------|-------------|
| General Work Item | Generic task, any workstream |
| Pro Incident | Privacy incident (ProPharma/HSBC) |
| Pro Assessment | Privacy assessment work |
| Home Task | Personal or household task |
| Home Career | Career opportunity |
| Masonic Task | Masonic duty or planning |

## Task ID Format

```
GFP-<WORKSTREAM>-<INITIATIVE>-<NUMBER>

Examples:
- GFP-PP-INC-001 — ProPharma Incident
- GFP-HB-TIA-002 — HSBC Transfer Assessment
- GFP-HM-CAR-003 — Home Career task
- GFP-MS-CAMH-004 — Masonic Comms
```

## Status Flow

```
Inbox → Ready → In Progress → Waiting → Blocked → Review → Done
                ↓
            Deferred → Abandoned
```

## Priority Definitions

| Code | Definition |
|------|------------|
| P0 | Must complete today (urgent) |
| P1 | Must complete this week (high) |
| P2 | Should complete this fortnight (medium) |
| P3 | Backlog, no deadline (low) |
| P4 | Future-dated, waiting (scheduled) |

## Project Fields

- **Status** — Workflow state
- **GFP Priority** — P0-P4
- **Workstream** — ProPharma, HSBC, Home, Masonic
- **Initiative** — 23 approved initiatives
- **Task ID** — GFP-XXX-XXX-NNN format
- **Due Date** — Target completion
- **Next Action** — Immediate next step
- **Assignees** — Owner

---

*Last updated: 2026-03-26*
