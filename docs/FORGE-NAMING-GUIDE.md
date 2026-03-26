# Forge Naming Guide

Clear naming conventions for the Forge ecosystem.

---

## Core Concepts

| Concept | What It Is | Example |
|---------|------------|---------|
| **Forge** | Umbrella brand for all products/projects | Forge |
| **Forge Pipeline** | Master tracking/project management layer | `harkers/github-forge-pipeline` |
| **Forge Products** | Actual software products under Forge | `products/privacy-intake` |

---

## Naming Hierarchy

```
Forge (brand)
├── Forge Pipeline (tracking layer)
│   └── github-forge-pipeline (repo)
│
└── Products (delivered software)
    ├── privacy-intake-pack
    ├── display-forge
    └── rank-forge
```

---

## Repository Naming

### Tracking/Management

| What | Name Pattern | Example |
|------|--------------|---------|
| Pipeline/Tracking | `forge-pipeline` or `github-forge-pipeline` | `harkers/github-forge-pipeline` |
| Workspace config | `forge-config` or `forge-orchestra` | Local only |

### Products

| Type | Pattern | Example |
|------|---------|---------|
| Product repo | `{product-name}` or `forge-{product}` | `privacy-intake-pack` |
| Product in Forge monorepo | `products/{product-name}` | `products/privacy-intake` |

---

## Issue Naming (Forge Pipeline)

### Format

```
[GFP-<WORKSTREAM>-<INITIATIVE>-<NUMBER>] <Description>
```

### Examples

| Issue Title | Meaning |
|-------------|---------|
| `[GFP-PP-DPI-002] Phase 1: Foundation` | ProPharma / Data-Protection-Intake / #002 |
| `[GFP-PP-INC-001] Assess incident` | ProPharma / Incidents / #001 |
| `[GFP-HB-VND-003] Review vendor DPA` | HSBC / Vendors / #003 |
| `[GFP-HM-CAR-005] Update CV` | Home / Career / #005 |

### Workstream Codes

| Code | Workstream |
|------|------------|
| PP | Forge-ProPharma |
| HB | Forge-HSBC |
| HM | Forge-Home |
| MS | Forge-Masonic |

---

## Product vs Pipeline

| Term | Meaning | Example |
|------|---------|---------|
| **Privacy Intake Pack** | The actual software product | FastAPI app, database, Docker |
| **Forge Pipeline** | Tracking issues, phases, progress | GitHub issues, project board |
| **GFP-PP-DPI-002** | Issue tracking work on the product | "Phase 1: Foundation" |

**Key distinction:**
- **Product** = What you're building (privacy-intake-pack)
- **Pipeline** = How you track it (GitHub Forge Pipeline issues)

---

## When Names Collide

### Problem: "Forge Pipeline" vs "Forge Products"

| Context | Meaning |
|---------|---------|
| "Update Forge Pipeline" | Update the tracking repo |
| "Deploy privacy-intake" | Deploy the actual product |
| "Check Forge status" | Ambiguous — clarify which |

### Solution: Use Full Names

| Instead of | Say |
|------------|-----|
| "Forge Pipeline" | "GitHub Forge Pipeline" or "the pipeline" |
| "privacy-intake" | "privacy-intake-pack" or "the intake product" |
| "the project" | Use specific name |

---

## Label Naming (GitHub)

| Category | Pattern | Example |
|----------|---------|---------|
| Workstream | `workstream:{name}` | `workstream:propharma` |
| Priority | `priority:{level}` | `priority:high` |
| Status | `status:{state}` | `status:active` |
| Type | `type:{kind}` | `type:assessment` |

---

## Branch Naming

| Branch Type | Pattern | Example |
|-------------|---------|---------|
| Feature | `feature/{description}` | `feature/file-upload` |
| Fix | `fix/{description}` | `fix/validation-error` |
| Phase | `phase/{number}-{name}` | `phase/1-foundation` |

---

## Commit Messages

### For Products

```
feat: add file upload support for PDFs and Word docs

- Support .pdf, .doc, .docx files
- Add SHA256 hash verification
- Store in uploads/{case_ref}/
```

### For Pipeline Updates

```
[forge-pipeline] Add Phase 1 tracking for privacy-intake-pack

Created issues #29-#33 for phased roadmap.
```

---

## Quick Reference

| What | Name |
|------|------|
| Brand | Forge |
| Tracking layer | Forge Pipeline |
| Tracking repo | `github-forge-pipeline` |
| Product | privacy-intake-pack |
| Product location | `harkers/Forge/products/privacy-intake` |
| Issue tracking product | `GFP-PP-DPI-XXX` |

---

## Questions

**Q: Why "GitHub Forge Pipeline" instead of just "Forge Pipeline"?**
A: The repo name includes "github-" because it lives on GitHub. In conversation, "Forge Pipeline" or "the pipeline" is fine. The "GitHub" prefix disambiguates when referring to the repo specifically.

**Q: Should products have "forge-" prefix?**
A: Optional. `privacy-intake-pack` works. `forge-privacy-intake` also works. Use what's clearest in context.

**Q: What about submodules in Forge?**
A: Products live as submodules under `products/`. The path `products/privacy-intake` is clear enough — no "forge-" prefix needed.

---

*Last updated: 2026-03-26*