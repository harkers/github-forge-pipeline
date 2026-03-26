# MEMORY.md — GitHub Forge Pipeline

## Project Identity

**Project Code:** GFP-001  
**Master Shorthand:** GFP  
**Name:** GitHub Forge Pipeline — Project Management via GitHub  
**Type:** Project Management System  
**Status:** `active`  
**Created:** 2026-03-26

## Purpose

GitHub Forge Pipeline provides a single governed planning and tracking structure for work across all Forge workstreams using **GitHub as the system of record**.

GitHub Issues and Projects V2 serve as the master planning layer:
- One master GitHub Project for all tracked work
- Standardized workstreams: Forge-ProPharma, Forge-HSBC, Forge-Home, Forge-Masonic
- Consistent naming, numbering, and classification
- Issue templates for each work type
- Clear priority and status models

**Key principle:** GitHub is the source of truth. No separate database, no sync layer, no duplicate systems.

## Scope

| Workstream | Coverage |
|------------|----------|
| Forge-ProPharma | Privacy, governance, compliance activities |
| Forge-HSBC | Professional workstreams |
| Forge-Home | Personal organization, life admin, career |
| Forge-Masonic | Communications, mentoring, history |

## Architecture

```
GitHub Issues ◄──────► GitHub Projects V2 ◄──────► Views/Reports
      │                      │                        │
      ▼                      ▼                        ▼
Issue Templates        Custom Fields           Filters/Dashboards
Labels/Tags            Status/Priority          Export/Reporting
Assignees              Workstream/Initiative
```

**No backend. No sync. No database.** GitHub is the system of record.

## Key Documents

| Code | Document | Status |
|------|----------|--------|
| GFP-001 | Project Definition | Active |
| GFP-101 | Domain Architecture | Active |
| GFP-201 | Sync Specification | Obsolete |
| Handbook | Full Project Handbook | Active |

## Project Fields

| Field | Type | Purpose |
|-------|------|---------|
| Status | Single select | Workflow state |
| Priority | Single select | Urgency/importance |
| Workstream | Single select | Forge-ProPharma, Forge-HSBC, Forge-Home, Forge-Masonic |
| Initiative | Single select | Grouping within workstream |
| Task ID | Text | Stable tracking code (GFP-XXX) |
| Due Date | Date | Target completion |
| Risk State | Single select | At-risk tracking |

## Issue Templates

| Template | Work Type |
|----------|-----------|
| 01-general-work-item | Generic task |
| 02-pro-incident | Privacy incident (ProPharma) |
| 03-pro-incident-reporting | Incident reporting |
| 04-pro-vendor-subprocessor | Vendor/subprocessor |
| 05-pro-assessment | Privacy assessment |
| 06-pro-data-rights | Data rights request |
| 07-pro-ropa | ROPA activity |
| 08-home-task | Home task |
| 09-home-career | Career task |
| 10-masonic-task | Masonic task |
| 11-taxonomy-change | Taxonomy update |

## Status Model

```
inbox → triage → active → blocked → review → done
                    ↓
                deferred
                    ↓
                abandoned
```

## Priority Model

| Priority | Definition |
|----------|------------|
| urgent | Must complete today |
| high | Must complete this week |
| medium | Should complete this fortnight |
| low | Backlog, no deadline |
| scheduled | Future-dated, waiting |

## Technical Decisions

### 2026-03-26: GitHub as System of Record

**Decision:** Use GitHub Projects V2 as the sole project management system. No Forge Pipeline sync, no separate database.

**Rationale:**
- Eliminates sync complexity and failure modes
- GitHub Issues are the canonical source of truth
- Projects V2 provides views, filtering, grouping
- Issue templates standardize intake
- Labels/tags provide flexible categorization

### 2026-03-26: Workstream Structure

**Decision:** Four workstreams with consistent structure.

| Workstream | Code | Scope |
|------------|------|-------|
| Forge-ProPharma | PRO | Professional, privacy, compliance |
| Forge-HSBC | HSBC | Work-specific |
| Forge-Home | HOME | Personal, life admin |
| Forge-Masonic | MASON | Masonic duties |

### 2026-03-26: Forge Pipeline Web App Stopped

**Decision:** Stop the Forge Pipeline web app (titan:4174). This project now uses GitHub directly.

**Containers stopped:**
- forge-pipeline-web
- forge-pipeline-api
- forge-pipeline-postgres
- forge-pipeline-redis

## Next Actions

1. Create GitHub Project V2 with defined fields
2. Create repository labels for workstreams, priorities, statuses
3. Test issue templates
4. Set up project views (by workstream, by status, by priority)
5. Document taxonomy in GitHub Wiki

---

*Update this file with significant decisions, state changes, and lessons learned.*

<!-- MEMORY-STACK-HARDENED:START -->
## Memory routing
- Use retrieval, not preload.
- Durable facts -> `para/`
- Daily residue -> `memory/YYYY-MM-DD.md`
- Rules and guardrails -> `AGENTS.md`
- Optional semantic acceleration -> QMD
- Canonical truth stays in files.
<!-- MEMORY-STACK-HARDENED:END -->