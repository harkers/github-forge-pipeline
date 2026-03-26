# GFP-IMPL-001 — Phased Implementation Plan

**Status:** Draft
**Created:** 2026-03-26
**Project:** GitHub Forge Pipeline

---

## Overview

This document defines the phased implementation plan for GitHub Forge Pipeline, transforming the handbook and design documentation into a fully operational project management system using GitHub as the system of record.

## Implementation Phases

| Phase | Focus | Duration | Status |
|-------|-------|----------|--------|
| Phase 1 | Repository & Project Setup | 1 day | Not Started |
| Phase 2 | Taxonomy & Labels | 1 day | Not Started |
| Phase 3 | Issue Templates | 1 day | Not Started |
| Phase 4 | Project Fields & Views | 1 day | Not Started |
| Phase 5 | Seed Items & Testing | 1 day | Not Started |
| Phase 6 | Documentation & Wiki | 1 day | Not Started |
| Phase 7 | Automation & CLI | 2 days | Not Started |

**Total Estimated Duration:** 8 days

---

## Phase 1: Repository & Project Setup

**Objective:** Establish the GitHub repository and GitHub Projects V2 foundation.

### Tasks

| Task | Description | Status |
|------|-------------|--------|
| 1.1 | Create GitHub repository (done: `github-forge-pipeline`) | Done |
| 1.2 | Create GitHub Projects V2 project | Not Started |
| 1.3 | Configure repository description and topics | Not Started |
| 1.4 | Set default branch to `main` | Done |
| 1.5 | Add README.md with project overview | Not Started |
| 1.6 | Add LICENSE file (MIT) | Not Started |
| 1.7 | Create `.gitignore` for common exclusions | Not Started |

### Deliverables

- GitHub repository configured
- GitHub Projects V2 created (empty)
- Basic repository files in place

### Commands

```bash
# Repository already exists: github.com/harkers/github-forge-pipeline

# Create GitHub Project V2 (requires gh CLI)
gh project create --owner harkers --title "GitHub Forge Pipeline" --body "Master planning and tracking for Forge workstreams"
```

---

## Phase 2: Taxonomy & Labels

**Objective:** Implement the complete label taxonomy for workstreams, priorities, statuses, and types.

### Workstream Labels

| Label | Color | Description |
|-------|-------|-------------|
| `workstream:propharma` | `#0E8A16` (green) | Forge-ProPharma work |
| `workstream:hsbc` | `#1D76DB` (blue) | Forge-HSBC work |
| `workstream:home` | `#D4C5F9` (purple) | Forge-Home work |
| `workstream:masonic` | `#FBCA04` (yellow) | Forge-Masonic work |

### Priority Labels

| Label | Color | Description |
|-------|-------|-------------|
| `priority:urgent` | `#B60205` (red) | P0 - Must complete today |
| `priority:high` | `#D93F0B` (orange) | P1 - Must complete this week |
| `priority:medium` | `#FBCA04` (yellow) | P2 - Should complete this fortnight |
| `priority:low` | `#0E8A16` (green) | P3 - Backlog, no deadline |
| `priority:scheduled` | `#1D76DB` (blue) | P4 - Future-dated, waiting |

### Status Labels

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

### Type Labels

| Label | Color | Description |
|-------|-------|-------------|
| `type:incident` | `#B60205` (red) | Privacy incident |
| `type:assessment` | `#D4C5F9` (purple) | Privacy assessment |
| `type:vendor` | `#1D76DB` (blue) | Vendor-related |
| `type:ropa` | `#0E8A16` (green) | ROPA activity |
| `type:data-rights` | `#FBCA04` (yellow) | Data rights request |
| `type:task` | `#EDEDED` (gray) | General task |

### Initiative Labels (Optional)

Create labels for each initiative if fine-grained filtering is needed:

| Label Pattern | Examples |
|---------------|----------|
| `initiative:incidents` | `initiative:incidents`, `initiative:vendors` |
| `initiative:career` | `initiative:career`, `initiative:maintenance` |

### Tasks

| Task | Description | Status |
|------|-------------|--------|
| 2.1 | Create workstream labels | Not Started |
| 2.2 | Create priority labels | Not Started |
| 2.3 | Create status labels | Not Started |
| 2.4 | Create type labels | Not Started |
| 2.5 | Create initiative labels (optional) | Not Started |

### Commands

```bash
# Workstream labels
gh label create "workstream:propharma" --color 0E8A16 --description "Forge-ProPharma work"
gh label create "workstream:hsbc" --color 1D76DB --description "Forge-HSBC work"
gh label create "workstream:home" --color D4C5F9 --description "Forge-Home work"
gh label create "workstream:masonic" --color FBDA04 --description "Forge-Masonic work"

# Priority labels
gh label create "priority:urgent" --color B60205 --description "P0 - Must complete today"
gh label create "priority:high" --color D93F0B --description "P1 - Must complete this week"
gh label create "priority:medium" --color FBCA04 --description "P2 - Should complete this fortnight"
gh label create "priority:low" --color 0E8A16 --description "P3 - Backlog, no deadline"
gh label create "priority:scheduled" --color 1D76DB --description "P4 - Future-dated, waiting"

# Status labels
gh label create "status:inbox" --color BFD4F2 --description "Newly captured, untriaged"
gh label create "status:triage" --color C5DEF5 --description "Awaiting classification"
gh label create "status:active" --color 0E8A16 --description "In progress"
gh label create "status:blocked" --color B60205 --description "Blocked on dependency"
gh label create "status:review" --color D4C5F9 --description "Awaiting review"
gh label create "status:done" --color EDEDED --description "Completed"
gh label create "status:deferred" --color FBCA04 --description "Deferred"
gh label create "status:abandoned" --color 000000 --description "Abandoned"

# Type labels
gh label create "type:incident" --color B60205 --description "Privacy incident"
gh label create "type:assessment" --color D4C5F9 --description "Privacy assessment"
gh label create "type:vendor" --color 1D76DB --description "Vendor-related"
gh label create "type:ropa" --color 0E8A16 --description "ROPA activity"
gh label create "type:data-rights" --color FBCA04 --description "Data rights request"
gh label create "type:task" --color EDEDED --description "General task"
```

---

## Phase 3: Issue Templates

**Objective:** Verify and test issue templates are working correctly.

### Templates Available

| Template | File | Purpose |
|----------|------|---------|
| 01-general-work-item | `.github/ISSUE_TEMPLATE/01-general-work-item.yml` | Generic task |
| 02-pro-incident | `.github/ISSUE_TEMPLATE/02-pro-incident.yml` | Privacy incident (Pro) |
| 03-pro-incident-reporting | `.github/ISSUE_TEMPLATE/03-pro-incident-reporting.yml` | Incident reporting |
| 04-pro-vendor-subprocessor | `.github/ISSUE_TEMPLATE/04-pro-vendor-subprocessor.yml` | Vendor/subprocessor |
| 05-pro-assessment | `.github/ISSUE_TEMPLATE/05-pro-assessment.yml` | Privacy assessment |
| 06-pro-data-rights | `.github/ISSUE_TEMPLATE/06-pro-data-rights.yml` | Data rights |
| 07-pro-ropa | `.github/ISSUE_TEMPLATE/07-pro-ropa.yml` | ROPA activity |
| 08-home-task | `.github/ISSUE_TEMPLATE/08-home-task.yml` | Home task |
| 09-home-career | `.github/ISSUE_TEMPLATE/09-home-career.yml` | Career task |
| 10-masonic-task | `.github/ISSUE_TEMPLATE/10-masonic-task.yml` | Masonic task |
| 11-taxonomy-change | `.github/ISSUE_TEMPLATE/11-taxonomy-change.yml` | Taxonomy update |

### Tasks

| Task | Description | Status |
|------|-------------|--------|
| 3.1 | Verify templates are in `.github/ISSUE_TEMPLATE/` | Done |
| 3.2 | Test each template creates correctly | Not Started |
| 3.3 | Add default assignees if needed | Not Started |
| 3.4 | Verify template selection UI works | Not Started |

### Validation

```bash
# Test template rendering locally
gh issue create --template 01-general-work-item.yml --title "[TEST] Template test" --body "Testing template rendering"

# Clean up test issue after validation
```

---

## Phase 4: Project Fields & Views

**Objective:** Configure GitHub Projects V2 with the complete field model and views.

### Required Fields

| Field | Type | Values |
|-------|------|--------|
| Status | Single Select | Inbox, Ready, In Progress, Waiting, Blocked, Review, Done, Deferred, Abandoned |
| Priority | Single Select | P0, P1, P2, P3, P4 |
| Workstream | Single Select | Forge-ProPharma, Forge-HSBC, Forge-Home, Forge-Masonic |
| Initiative | Single Select | (See initiative definitions) |
| Task ID | Text | GFP-XXX-XXX-NNN format |
| Due Date | Date | Target completion |
| Next Action | Text | Immediate next step |
| Owner | Assignee | Responsible person |
| Notes | Text | Context and working notes |

### Optional Fields

| Field | Type | Values |
|-------|------|--------|
| Impact | Single Select | High, Medium, Low |
| Risk | Single Select | High, Medium, Low |
| Waiting On | Text | Blocking dependency |
| External Deadline | Date | External deadline |
| Link | Text | Related URL/reference |
| Vendor Name | Text | Vendor for vendor tasks |
| Business Area | Text | Related business function |
| Assessment Type | Single Select | DPIA, TIA, LIA, Legal, Other |
| Incident Severity | Single Select | S1, S2, S3, S4 |
| Notification Required | Single Select | Yes, No, TBD |

### Project Views

| View | Purpose | Group By | Sort By |
|------|---------|----------|---------|
| All Work | Full visibility | Workstream | Priority, Due Date |
| P0/P1 Focus | Immediate priority | Priority | Due Date |
| This Week | Near-term planning | Status | Due Date |
| Waiting | Blocked work | Initiative | Priority |
| Forge-ProPharma | Pro workstream | Initiative | Priority |
| Forge-HSBC | HSBC workstream | Initiative | Priority |
| Forge-Home | Personal workstream | Initiative | Priority |
| Forge-Masonic | Masonic workstream | Initiative | Priority |
| Incidents | Incident casework | Status | Priority |
| Vendors | Vendor work | Status | Due Date |
| Assessments | Assessment work | Status | Due Date |
| Done | Completion history | Workstream | Date |

### Tasks

| Task | Description | Status |
|------|-------------|--------|
| 4.1 | Create Status field with values | Not Started |
| 4.2 | Create Priority field with values | Not Started |
| 4.3 | Create Workstream field with values | Not Started |
| 4.4 | Create Initiative field with values | Not Started |
| 4.5 | Create Task ID field | Not Started |
| 4.6 | Create Due Date field | Not Started |
| 4.7 | Create Next Action field | Not Started |
| 4.8 | Create Notes field | Not Started |
| 4.9 | Create optional fields | Not Started |
| 4.10 | Create all views | Not Started |

### Commands (GraphQL API)

```bash
# Create project fields via gh CLI (requires project number)
# Note: GitHub Projects V2 field creation requires GraphQL API

# Example: Add Status field
gh api graphql -f query='
  mutation {
    createProjectV2Field(input: {
      projectId: "PROJECT_ID"
      name: "Status"
      dataType: SINGLE_SELECT
      singleSelectOptions: [
        {name: "Inbox", color: "BLUE"}
        {name: "Ready", color: "GRAY"}
        {name: "In Progress", color: "GREEN"}
        {name: "Waiting", color: "YELLOW"}
        {name: "Blocked", color: "RED"}
        {name: "Review", color: "PURPLE"}
        {name: "Done", color: "GRAY"}
        {name: "Deferred", color: "YELLOW"}
        {name: "Abandoned", color: "GRAY"}
      ]
    }) {
      projectV2Field {
        id
        name
      }
    }
  }
'
```

---

## Phase 5: Seed Items & Testing

**Objective:** Create initial items to validate the system works as designed.

### Seed Items

| Task ID | Title | Workstream | Initiative | Priority | Status |
|---------|-------|------------|------------|----------|--------|
| GFP-PP-INB-001 | Example: Initial ProPharma inbox item | Forge-ProPharma | Inbox | P2 | Inbox |
| GFP-PP-INC-001 | Example: Assess confidentiality incident | Forge-ProPharma | Incidents | P0 | Ready |
| GFP-HB-INB-001 | Example: Initial HSBC inbox item | Forge-HSBC | Inbox | P2 | Inbox |
| GFP-HB-TIA-001 | Example: Complete transfer impact assessment | Forge-HSBC | Transfer-Impact-Assessments | P1 | In Progress |
| GFP-HM-INB-001 | Example: Initial Home inbox item | Forge-Home | Inbox | P3 | Inbox |
| GFP-HM-CAR-001 | Example: Update CV and send to recruiter | Forge-Home | Career | P1 | Ready |
| GFP-MS-INB-001 | Example: Initial Masonic inbox item | Forge-Masonic | Inbox | P3 | Inbox |

### Tasks

| Task | Description | Status |
|------|-------------|--------|
| 5.1 | Create 10 seed items across workstreams | Not Started |
| 5.2 | Verify items appear in correct views | Not Started |
| 5.3 | Test filtering by workstream | Not Started |
| 5.4 | Test filtering by priority | Not Started |
| 5.5 | Test filtering by status | Not Started |
| 5.6 | Verify Task ID format | Not Started |
| 5.7 | Test issue templates create correctly | Not Started |

---

## Phase 6: Documentation & Wiki

**Objective:** Create GitHub Wiki documentation for easy reference.

### Wiki Pages

| Page | Content |
|------|---------|
| Home | Overview and quick start |
| Workstreams | Workstream definitions |
| Initiatives | Initiative definitions and codes |
| Naming Standard | Code format and naming rules |
| Field Model | Project fields and values |
| Views | View purposes and configuration |
| Issue Templates | Template usage guide |
| Change Control | How to request taxonomy changes |

### Tasks

| Task | Description | Status |
|------|-------------|--------|
| 6.1 | Enable GitHub Wiki | Not Started |
| 6.2 | Create Home page | Not Started |
| 6.3 | Create Workstreams page | Not Started |
| 6.4 | Create Initiatives page | Not Started |
| 6.5 | Create Naming Standard page | Not Started |
| 6.6 | Create Field Model page | Not Started |
| 6.7 | Create Views page | Not Started |
| 6.8 | Create Issue Templates page | Not Started |
| 6.9 | Create Change Control page | Not Started |

---

## Phase 7: Automation & CLI

**Objective:** Create CLI tooling for repeatable setup and automation.

### CLI Commands

| Command | Purpose |
|---------|---------|
| `gfp init` | Initialize project with fields, views, labels |
| `gfp label create-all` | Create all labels |
| `gfp field create-all` | Create all project fields |
| `gfp view create-all` | Create all project views |
| `gfp item new` | Create new item with proper format |
| `gfp item list` | List items with filters |
| `gfp report weekly` | Generate weekly report |

### Tasks

| Task | Description | Status |
|------|-------------|--------|
| 7.1 | Create `gfp` CLI tool (Python/Node) | Not Started |
| 7.2 | Implement `init` command | Not Started |
| 7.3 | Implement `label create-all` command | Not Started |
| 7.4 | Implement `field create-all` command | Not Started |
| 7.5 | Implement `view create-all` command | Not Started |
| 7.6 | Implement `item new` command | Not Started |
| 7.7 | Implement `report weekly` command | Not Started |
| 7.8 | Document CLI in README | Not Started |

---

## Success Criteria

| Criteria | Definition |
|----------|------------|
| Labels | All 25+ labels created and available |
| Fields | All required fields configured in Project |
| Views | All 12 views created and functional |
| Templates | All 11 templates tested and working |
| Seed Items | 10+ items created with correct format |
| Wiki | All 9 pages published |
| CLI | Basic commands working |

---

## Risk Log

| Risk | Impact | Mitigation |
|------|--------|------------|
| GitHub Projects V2 API limits | High | Use GraphQL batch operations |
| Label color conflicts | Low | Define explicit hex colors |
| Field value mismatches | Medium | Validate against handbook |
| Initiative list changes | Medium | Document change process |

---

## Next Actions

1. **Phase 1:** Verify repository is ready, create GitHub Project V2
2. **Phase 2:** Create all labels using `gh label create` commands
3. **Phase 3:** Test issue templates
4. **Phase 4:** Configure project fields and views
5. **Phase 5:** Create seed items
6. **Phase 6:** Create Wiki documentation
7. **Phase 7:** Build CLI tooling

---

## Appendix: Initiative Codes Reference

### ProPharma & HSBC

| Code | Initiative |
|------|------------|
| INB | Inbox |
| DPI | Data-Protection-Intake |
| INC | Incidents |
| IRP | Incident-Reporting |
| VND | Vendors |
| SPL | Sub-Processor-List |
| ROP | ROPA |
| DRT | Data-Rights |
| LGA | Legislation-Assessments |
| LIA | Legitimate-Interest-Assessments |
| PIA | Privacy-Impact-Assessments |
| TIA | Transfer-Impact-Assessments |

### Home

| Code | Initiative |
|------|------------|
| INB | Inbox |
| LIFE | Life-Easier |
| CAR | Career |
| MAINT | Maintenance |
| GARD | Garden |
| COV | Cover |
| TRAV | Travel |
| HLTH | Health |

### Masonic

| Code | Initiative |
|------|------------|
| INB | Inbox |
| CAMH | Comms-AMH |
| MENT | Mentoring |
| HIST | History |
| OFF | Officers |

---

*End of Implementation Plan*