# Coding Standards

Standards and principles for all code in the {{PROJECT_NAME}} platform.

<!-- Default stack: Python 3.11+ (FastAPI) backend, SvelteKit frontend, Terraform + GCP infrastructure -->

---

## Coding Principles

These principles are non-negotiable. AI agents and human developers must follow them.

### Boy Scout Rule
Leave code better than you found it. When touching a file, fix nearby small issues — stale comments, inconsistent naming, missing type hints. Don't let entropy accumulate.

### Test-First Development
Write a failing test before implementing new functionality. Run it — confirm it fails. Implement until green. This applies to bug fixes too: write a test that reproduces the bug first.

### YAGNI (You Aren't Gonna Need It)
Don't build abstractions, helpers, or features until there is a concrete, immediate need. No speculative interfaces. No "just in case" parameters. The simplest solution that works is the correct one.

### Single Responsibility Principle
Each function does one thing. Each module owns one concern. Each service handles one domain. When a function needs an "and" in its description, split it.

### Fail Fast
Surface errors immediately. Never silently swallow exceptions. Validate inputs at system boundaries (user input, API calls, external data). Internal code trusts internal contracts.

### Verification Loop
Code is not "done" until tests pass in the terminal. After any code change:
1. Run relevant tests in the terminal
2. If tests fail → fix and re-run (up to 3 attempts, then report to user)
3. If no tests exist for the changed code → write them first (test-first)
4. Only declare "done" after a green test run

---

## Backend Standards

<!-- Default: Python 3.11+ (FastAPI). Customize for your stack. -->

- **Style:** Follow PEP 8. Use `ruff` for linting and formatting.
- **Typing:** Type hints required on all function signatures. Use Pydantic for data validation.
- **Async:** Prefer `async def` for I/O-bound endpoints.
- **Logging:** Use Python's standard `logging` module. No custom logger wrappers.
- **Error Handling:** Raise specific exceptions. Use FastAPI exception handlers. Never return bare 500s.

## Frontend Standards

<!-- Default: SvelteKit + TypeScript. Customize for your stack. -->

- **Framework:** {{TECH_STACK_FRONTEND}}
- **Language:** TypeScript strict mode. No `any` types without justification.
- **Components:** Prefer small, composable Svelte components. One component per file.
- **State:** Use Svelte stores for shared state. Avoid prop drilling beyond 2 levels.
- **Styling:** Follow `docs/DESIGN_SYSTEM.md` patterns. Use CSS variables for theming.

## Infrastructure Standards

<!-- Default: Terraform + GCP. Customize for your stack. -->

- **IaC Only:** All infrastructure defined in `{{INFRA_DIR}}/` Terraform modules. {{CI_RESTRICTIONS}}
- **Docs Sync:** When adding or modifying infrastructure resources, update `docs/ARCHITECTURE.md` (between `<!-- INFRA-START -->` and `<!-- INFRA-END -->` markers).
- **No Manual Resources:** Never use CLI commands or console clicks to create persistent resources that Terraform can manage.

## Dependency Constraints

- **Banned:** {{BANNED_DEPENDENCIES}}
- **Preferred:** Always prioritize {{PREFERRED_SERVICES}} over external third-party tools.
- **New Dependencies:** Adding a new dependency is a HIGH-RISK change — requires user approval before proceeding.

---

## Directory Structure

<!-- Customize for your project layout -->

```
project-root/
├── AGENTS.md                       # Cross-agent instructions
├── .github/
│   ├── copilot-instructions.md     # Copilot-specific instructions
│   ├── agents/                     # Specialist AI agents
│   └── instructions/               # Scoped instruction files
├── docs/
│   ├── VISION.md
│   ├── ARCHITECTURE.md
│   ├── STANDARDS.md
│   ├── CONTRIBUTING.md
│   ├── DESIGN_SYSTEM.md
│   ├── DATA_DICTIONARY.md
│   ├── CHANGELOG.md
│   ├── MCP_SETUP.md
│   ├── prd/
│   ├── decisions/
│   └── archive/
├── src/           # or service-specific folders
└── tests/
```

## Development Workflow

- **Atomic Commits:** One logical change per commit. Use conventional commit messages.
- **CI First:** Pipelines (linter, tests) must run on every commit. Unverified code does not exist.
- **Micro-Tasks:** Break complex work into verifiably complete steps.
- **Track Issues in GitHub:** Bugs, features, and backlog items are tracked as GitHub Issues — not markdown files.

## Documentation Hygiene

- **Debt Tracking:** All technical debt is tracked as GitHub Issues with `tech-debt` label and severity. Report all compromises immediately.
- **Changelog:** Auto-generated from conventional commits. Write detailed, meaningful commit messages.
- **Archive Policy:** Archive folder preserves historical context without cluttering active docs.
