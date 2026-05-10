---
name: 'ADR Standards'
description: 'Architecture Decision Record conventions'
applyTo: 'docs/decisions/**'
---

# Architecture Decision Record Conventions

Reference: `docs/decisions/ADR-TEMPLATE.md` for the full template.

## When to Create an ADR

Create an ADR when a decision:
- Changes system architecture or service boundaries
- Introduces or removes a dependency
- Affects multiple services or teams
- Has long-term implications that would be costly to reverse
- Reverses or supersedes a previous decision

## Decision Format

When presenting architectural choices:

1. **Present 2-3 Options minimum** with pros, cons, effort, and risk for each
2. **State your recommendation** with weighted reasoning referencing `docs/VISION.md` and `docs/ARCHITECTURE.md`
3. **Wait for user approval** — never proceed without confirmation (HIGH-RISK per autonomy model)

## ADR Lifecycle
```
Proposed → Accepted → [Deprecated | Superseded by ADR-XXX]
```

## Naming Convention
`ADR-XXX-decision-slug.md` — sequential three-digit numbering. Check existing ADRs in `docs/decisions/` for the next number.
