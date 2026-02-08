# Technical Debt Log

*See `.github/copilot-instructions.md` for the Debt Protocol.*

> **Bug vs Debt Distinction:**
> - **Bugs** → [`BUGS.md`](BUGS.md): Broken behavior — something doesn't work as intended.
> - **Debt** → This file: Known shortcuts — works but needs improvement.
>
> **New entries** should use sequential IDs (`DEBT-XXX`). Existing entries without IDs are grandfathered.

## Severity Definitions

| Severity | Definition | Action |
|----------|------------|--------|
| **HIGH** | Security risk or architectural violation | Must be addressed before next release |
| **Medium** | Code quality or performance concern | Address within 2 sprints |
| **Low** | Minor improvement or polish | Backlog for future sprints |

## Debt Registry

| ID | Severity | Date | Component | Description | Plan to Fix |
|----|----------|------|-----------|-------------|-------------|
| *DEBT-001* | *Medium* | *YYYY-MM-DD* | *example-service* | *Example: Hardcoded configuration value* | *Move to environment variable* |

<!-- Add new entries at the TOP of the table (most recent first) -->
