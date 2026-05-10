# {{PROJECT_NAME}} — AI Agent Instructions

<!-- This file is automatically loaded by VS Code Copilot, Claude Code, and other AI agents. -->
<!-- It contains the portable, cross-agent project identity and rules. -->

## Project Identity

- **Project:** {{PROJECT_NAME}}
- **Phase:** {{CURRENT_PHASE}}
- **Target:** {{TARGET_PLATFORM}} ({{DEPLOY_REGION}})

| Layer | Technology |
|-------|------------|
| Backend | {{TECH_STACK_BACKEND}} |
| Frontend | {{TECH_STACK_FRONTEND}} |
| Infrastructure | {{TECH_STACK_INFRA}} |
| Database | {{TECH_STACK_DB}} |
| AI | {{TECH_STACK_AI}} |

<!-- Default stack: Python 3.11+ (FastAPI), SvelteKit, Terraform + GCP, Cloud SQL / Firestore, Vertex AI -->

## Core Values

All work must align with the principles in `docs/VISION.md`:
{{VISION_VALUES}}

---

## Autonomy Model (Tiered)

The user always has the final say. AI agents follow a tiered autonomy model:

### HIGH-RISK (propose + wait for approval)
- Architecture changes or new design patterns
- Adding, removing, or upgrading dependencies
- Infrastructure modifications (Terraform, cloud resources)
- PRDs and planning decisions
- Deleting files or branches
- Changes to shared config (CI/CD, deployment, secrets)

### LOW-RISK (auto-execute)
- Bug fixes within existing patterns
- Writing and running tests
- Refactors that don't change external behavior
- Documentation updates
- Formatting and linting fixes

When in doubt, **propose and wait**.

---

## Coding Principles

Follow the principles defined in `docs/STANDARDS.md`. The key rules:

1. **Boy Scout Rule** — Leave code better than you found it
2. **Test-First** — Write a failing test before implementing
3. **YAGNI** — Don't build it until you need it
4. **Single Responsibility** — Each function/module does one thing
5. **Fail Fast** — Surface errors immediately, never swallow exceptions
6. **Verification Loop** — Code is not "done" until tests pass in the terminal

---

## Verification Loop Protocol

After any code change, you MUST:

1. Run relevant tests in the terminal
2. If tests fail → fix and re-run (up to 3 attempts)
3. If no tests exist for changed code → write them first (test-first)
4. Only declare "done" after a green test run
5. If tests cannot pass after 3 attempts → report to user with findings

This is non-negotiable. Never skip verification.

---

## Pre-Commit Protocol

When ready to commit, suggest a conventional commit message:

- **Format:** `<type>(<scope>): <description>`
- **Types:** `feat`, `fix`, `refactor`, `docs`, `chore`, `test`, `ci`
- **Scope:** Service, module, or area (e.g., `api`, `frontend`, `infra`)
- **Description:** Imperative mood, lowercase, no period
- **Body:** Reference GitHub Issue numbers. Explain *why*, not just *what*.

---

## Reference Documents

| Document | Purpose |
|----------|---------|
| `docs/VISION.md` | Product mission and core values |
| `docs/ARCHITECTURE.md` | System design and service boundaries |
| `docs/STANDARDS.md` | Coding principles, conventions, banned dependencies |
| `docs/CONTRIBUTING.md` | PR process, commit conventions, team workflow |
| `docs/DESIGN_SYSTEM.md` | UI patterns, colors, typography |
| `docs/DATA_DICTIONARY.md` | Canonical field names and schemas |
| `docs/CHANGELOG.md` | Auto-generated from conventional commits |
| `docs/MCP_SETUP.md` | MCP server configuration guide |

---

## MCP Tools

AI agents have access to external tools via Model Context Protocol (MCP):

{{MCP_TOOLS_TABLE}}

<!-- Example:
| Server | Tools | Used By |
|--------|-------|---------|
| **GitHub** | Issues, PRs, code search | Bug Hunter, Code Reviewer, PRD Architect |
| **Chrome DevTools** | Screenshots, console, network, DOM | Bug Hunter, RCA Worker |
| **GCP** | Cloud Run, BigQuery, Firebase | Terraform Guardian |
-->

See `docs/MCP_SETUP.md` for configuration instructions.

---

## Issue Tracking

All bugs, features, and backlog items are tracked as **GitHub Issues** — not markdown files.

- **Bugs:** Create issues with `bug` label and priority (`P0`–`P3`)
- **Features:** Create issues with `enhancement` label
- **Tech Debt:** Create GitHub Issues with `tech-debt` label and severity (`critical`, `high`, `medium`, `low`)
- **Sprint Planning:** Use GitHub Projects for prioritization
