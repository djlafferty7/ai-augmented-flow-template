# Coding Guidelines

## Backend Standards

<!-- Customize to your backend language/framework -->

- **Style:** Follow standard style guide (e.g., PEP8 for Python, ESLint for Node.js)
- **Logging:** Use standard logging framework. Avoid custom logger wrappers.
- **Async:** Prefer async patterns where supported.
- **Typing:** Use type hints/annotations for data validation.

## Frontend Standards

<!-- Customize to your frontend framework -->

- **Framework:** {{TECH_STACK_FRONTEND}}
- **State:** [State management approach]
- **Components:** [Component patterns — functional, class-based, etc.]

## Directory Structure

<!-- Define your standard project layout -->

```
project-root/
├── .github/
│   └── copilot-instructions.md
├── docs/
│   ├── VISION.md
│   ├── ARCHITECTURE.md
│   ├── GUIDELINES.md
│   ├── DESIGN_SYSTEM.md
│   ├── TECHNICAL_DEBT.md
│   ├── BUGS.md
│   ├── DEV_JOURNAL.md
│   ├── BACKLOG.md
│   ├── prd/
│   ├── decisions/
│   └── archive/
├── src/           # or service-specific folders
└── tests/
```

## Workflow Rules

1.  **No Silent Failures:** Explicit error handling. Log and surface errors appropriately.
2.  **Debt Protocol:** If you must hack, log it in `TECHNICAL_DEBT.md`.

## Development Workflow

- **Atomic Commits:** Every Backlog Story corresponds to at least one Git Commit/Push. Do not batch multiple stories into one PR.
- **CI First:** Pipelines (linter, tests) must run on every commit. Unverified code does not exist.
- **Micro-Tasks:** Break complex setups into verifiably complete steps.
- **Infrastructure as Code:** {{CI_RESTRICTIONS}}
- **Infrastructure Docs Sync:** When adding or modifying infrastructure resources, update the `## Infrastructure` section in `docs/ARCHITECTURE.md` (between `<!-- INFRA-START -->` and `<!-- INFRA-END -->` markers).

## Documentation Hygiene

- **Live Journaling:** The `DEV_JOURNAL.md` is a living document. Every completed task must be logged.
- **Debt Registry:** `TECHNICAL_DEBT.md` is not a shame list; it is a management tool. Report all compromises immediately.

## Documentation Archive Policy

- **DEV_JOURNAL:** Archive entries older than 2 weeks monthly to `docs/archive/DEV_JOURNAL_YYYY-MM.md`.
- **BACKLOG:** Move fully-completed Epics to `docs/archive/BACKLOG_COMPLETED.md`.
- **TECHNICAL_DEBT:** Move resolved items to `docs/archive/TECHNICAL_DEBT_RESOLVED.md`.
- **Archive folder:** `docs/archive/` — preserves historical context without cluttering active docs.
