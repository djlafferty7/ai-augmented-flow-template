# AI-Augmented Development Framework

A structured template for building software projects with AI coding assistants (GitHub Copilot, Claude, etc.). This framework enforces architectural consistency, documentation hygiene, and disciplined development workflows through a layered instruction system and specialist agents.

## What This Is

- **Layered AI Instructions** — AGENTS.md → copilot-instructions.md → scoped .instructions.md
- **7 Specialist Agents** — Bug Hunter, Code Reviewer, PRD Architect, Terraform Guardian, and more
- **GitHub-Native Tracking** — Issues for bugs, backlog, and debt (via GitHub MCP)
- **Tiered Autonomy** — AI proposes high-risk changes, auto-executes low-risk ones
- **PRD & ADR Templates** — Structured feature requests and architectural decisions

## Structure

```
AGENTS.md                          # Cross-agent instructions (always loaded)
SETUP_TEMPLATE.md                  # Setup guide (delete after customizing)

.github/
├── copilot-instructions.md        # Copilot-specific agent config
├── agents/                        # Specialist agents
│   ├── bug-hunter.agent.md
│   ├── code-reviewer.agent.md
│   ├── debt-logger.agent.md
│   ├── decision-architect.agent.md
│   ├── prd-architect.agent.md
│   ├── rca-worker.agent.md
│   └── terraform-guardian.agent.md
└── instructions/                  # Scoped instructions (auto-applied by file type)
    ├── backend.instructions.md    # *.py
    ├── frontend.instructions.md   # *.svelte, *.ts, *.css
    ├── terraform.instructions.md  # *.tf
    ├── testing.instructions.md    # *test*, *spec*
    ├── prd.instructions.md        # docs/prd/**
    └── decisions.instructions.md  # docs/decisions/**

docs/
├── VISION.md                      # Product vision & core values
├── ARCHITECTURE.md                # Technical architecture & infrastructure
├── STANDARDS.md                   # Coding standards, principles & workflow rules
├── DESIGN_SYSTEM.md               # UI/UX patterns & visual standards
├── DATA_DICTIONARY.md             # Canonical field names & schemas
├── SETUP.md                       # Developer setup & deployment
├── CONTRIBUTING.md                # Contribution guidelines
├── CHANGELOG.md                   # Auto-generated from conventional commits
├── MCP_SETUP.md                   # MCP server configuration guide
├── prd/
│   └── PRD-TEMPLATE.md            # Feature request template
├── decisions/
│   └── ADR-TEMPLATE.md            # Architecture decision record
└── archive/                       # Historical entries
```

## Quick Start

1. **Use this template** (click "Use this template" on GitHub) or clone it
2. **Run find-and-replace** for all `{{PLACEHOLDER}}` values (see `SETUP_TEMPLATE.md`)
3. **Set up MCP servers** — follow `docs/MCP_SETUP.md` (GitHub MCP required)
4. **Customize** your tech stack in `AGENTS.md`, `docs/STANDARDS.md`, and `docs/ARCHITECTURE.md`
5. **Define** your core values in `docs/VISION.md`
6. **Create initial GitHub Issues** for your backlog
7. **Delete** `SETUP_TEMPLATE.md` when ready

See [`SETUP_TEMPLATE.md`](SETUP_TEMPLATE.md) for the full setup guide, placeholder reference, and verification checklist.

## Instruction Architecture

Instructions are loaded in layers, each adding specificity:

| Layer | File(s) | Scope | Loaded |
|-------|---------|-------|--------|
| **1. Cross-Agent** | `AGENTS.md` | All agents, all files | Always |
| **2. Copilot-Specific** | `.github/copilot-instructions.md` | GitHub Copilot | Always (Copilot only) |
| **3. Scoped** | `.github/instructions/*.instructions.md` | Files matching `applyTo` glob | When editing matching files |

**AGENTS.md** contains project identity, tech stack, coding principles, the tiered approval model, and the verification loop. It's recognized by Copilot, Claude Code, and other agents.

## Tiered Autonomy Model

The framework uses a two-tier approval model — AI has freedom for safe changes but must ask for risky ones:

| Category | Examples | AI Behavior |
|----------|----------|-------------|
| **HIGH-RISK** (propose + wait) | Architecture changes, new dependencies, infra modifications, PRDs, file/branch deletion | AI proposes a plan and waits for user approval |
| **LOW-RISK** (auto-execute) | Bug fixes, test writing, refactoring, documentation, formatting | AI executes and reports results |

Core principle: **User always has final say.** AI proposes, humans approve.

## Coding Principles

All agents follow these principles (defined in `AGENTS.md`):

1. **Boy Scout Rule** — Leave code better than you found it
2. **Test-First** — Write/update tests before implementation
3. **YAGNI** — Don't build what isn't needed now
4. **Single Responsibility** — One reason to change per module
5. **Fail Fast** — Validate early, surface errors immediately
6. **Verification Loop** — Tests must pass before marking work complete

## Core Protocols

| Protocol | Triggers When | What Happens |
|----------|---------------|--------------|
| **6-Step Consistency** | Before any code generation | Validates against VISION, STANDARDS, DESIGN_SYSTEM, DATA_DICTIONARY |
| **Verification Loop** | After any code change | Run tests → fix failures → confirm green → commit |
| **Tiered Approval** | Before executing changes | Classifies risk level → auto-execute or propose + wait |
| **PRD Protocol** | New feature request | Interview → debt review → alternatives → draft → approval |
| **Debt Protocol** | Shortcut taken | Creates GitHub Issue with `tech-debt` label (halts for HIGH) |
| **Bug Protocol** | Bug discovered | Creates GitHub Issue with priority label (halts for P0/P1) |
| **Pre-Commit Protocol** | Ready to commit | Suggests conventional commit message |
| **Decision Protocol** | Architectural choice | Options table → recommendation → ADR |

## Specialist Agents

| Agent | Type | Description |
|-------|------|-------------|
| **Bug Hunter** | User-accessible | Systematic bug investigation → GitHub Issue creation with P0-P3 triage |
| **Code Reviewer** | User-accessible | PR review with Boy Scout Rule checks and verification loop |
| **Terraform Guardian** | User-accessible | IaC enforcement — blocks manual resource creation |
| **PRD Architect** | User-accessible | Interactive PRD creation with interview, debt review, and effort estimation |
| **RCA Worker** | Subagent | Read-only root cause analysis (5 Whys methodology) |
| **Debt Logger** | Subagent | Technical debt tracking with severity assessment + GitHub Issue |
| **Decision Architect** | Subagent | Options analysis with ADR creation |

Switch to user-accessible agents via the VS Code agent dropdown (`@agent-name`). Subagents are invoked automatically by other agents.

## MCP Servers

This template is designed to work with MCP (Model Context Protocol) servers for enhanced capabilities:

| Server | Purpose | Required? |
|--------|---------|-----------|
| **GitHub** | Issues, PRs, code search | Yes — core tracking |
| **Chrome DevTools** | Screenshots, console, DOM, network | Optional — debugging |
| **GCP** | Cloud Run, BigQuery, Firebase | Optional — if using GCP |

See [`docs/MCP_SETUP.md`](docs/MCP_SETUP.md) for configuration instructions.

## Compatibility

| Agent | AGENTS.md | copilot-instructions.md | .instructions.md |
|-------|-----------|------------------------|-------------------|
| **GitHub Copilot** | Yes | Yes | Yes |
| **Claude Code** | Yes | No | No |
| **Cursor** | Partial | No | No |

`AGENTS.md` is the portable layer — it works across agents. Copilot-specific features (scoped instructions, specialist agents) require VS Code + GitHub Copilot.

## Philosophy

1. **User Has Final Say** — AI proposes, humans approve. No autonomous high-risk changes.
2. **No Silent Shortcuts** — All debt and bugs are tracked via GitHub Issues, never hidden.
3. **Documentation Driven** — Code follows the docs, not the other way around.
4. **AI as Enforcer** — The AI assistant actively maintains standards, not just writes code.
5. **Minimum Viable Process** — Just enough structure to be useful, not so much it gets in the way.

## Inspired By

- [Architecture Decision Records (ADR)](https://adr.github.io/)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [The Twelve-Factor App](https://12factor.net/)
- [Google's Engineering Practices](https://google.github.io/eng-practices/)

## License

MIT — Use freely, adapt as needed.
