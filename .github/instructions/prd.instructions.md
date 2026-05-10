---
name: 'PRD Standards'
description: 'Product Requirements Document conventions'
applyTo: 'docs/prd/**'
---

# PRD Conventions

Reference: `docs/prd/PRD-TEMPLATE.md` for the full template, `docs/VISION.md` for core values alignment.

## PRD Protocol

### Before Writing a PRD
1. **Check for existing PRDs** — search `docs/prd/` for overlap
2. **Review open GitHub Issues** — search for related issues, feature requests, or bugs that could be addressed
3. **Search GitHub Issues labeled `tech-debt`** — identify debt items that could be resolved as part of this feature (Boy Scout Rule for planning)

### Creating a PRD
1. Copy `docs/prd/PRD-TEMPLATE.md` to `docs/prd/PRD-XXX-slug.md` (next sequential number)
2. Fill in all sections, with special attention to:
   - **Vision Alignment Checklist** — all core values must pass
   - **Architecture Impact** — services, database, API changes
   - **Tech Debt Opportunities** — GitHub Issues labeled `tech-debt` that can be resolved
   - **Alternatives Considered** — always present 2-3 options
   - **Effort Estimation** — T-shirt size (S/M/L/XL)

### PRD Approval Flow
- Present draft summary to user for approval
- User approves → create GitHub Issues for backlog items
- User requests changes → update and re-present
- User rejects → mark as "Rejected" in PRD status

## PRD Lifecycle
```
Draft → Review → Approved → GitHub Issues Created → Implementation → Done
```

## Naming Convention
`PRD-XXX-feature-slug.md` — sequential three-digit numbering.
