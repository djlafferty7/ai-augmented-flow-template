# AI-Augmented Development Framework

A structured template for building software projects with AI coding assistants (GitHub Copilot, Claude, etc.). This framework enforces architectural consistency, documentation hygiene, and disciplined development workflows.

## 🎯 What This Is

This template provides:

- **Copilot Instructions** — AI agent behavior rules that enforce your standards
- **7 Core Protocols** — Debt, Bug, PRD, Post-Task, Pre-Commit, Decision, Consistency
- **Living Documentation** — Journal, debt registry, bug tracker, backlog
- **PRD & ADR Templates** — Structured feature requests and architectural decisions

## 📁 Structure

```
.github/
└── copilot-instructions.md    # AI agent behavior configuration

docs/
├── VISION.md                  # Product vision & core values
├── ARCHITECTURE.md            # Technical architecture & infrastructure
├── GUIDELINES.md              # Coding standards & workflow rules
├── DESIGN_SYSTEM.md           # UI/UX patterns & visual standards
├── TECHNICAL_DEBT.md          # Living debt registry
├── BUGS.md                    # Bug tracking with priority levels
├── DEV_JOURNAL.md             # Reverse-chronological activity log
├── BACKLOG.md                 # Sprint/epic tracking
├── prd/
│   └── PRD-TEMPLATE.md        # Feature request template
├── decisions/
│   └── ADR-TEMPLATE.md        # Architecture decision record
└── archive/                   # Historical entries

SETUP_TEMPLATE.md              # Setup guide (delete after customizing)
README.md                      # This file
```

## 🚀 Quick Start

1. **Use this template** (click "Use this template" on GitHub) or clone it
2. **Run find-and-replace** for all `{{PLACEHOLDER}}` values (see `SETUP_TEMPLATE.md`)
3. **Customize** your tech stack in `GUIDELINES.md` and `ARCHITECTURE.md`
4. **Define** your core values in `VISION.md`
5. **Delete** `SETUP_TEMPLATE.md` when ready
6. **Start building** — the AI will follow your protocols

## 🔄 Core Protocols

| Protocol | Triggers When | What Happens |
|----------|---------------|--------------|
| **5-Step Consistency** | Before any code | Validates against VISION, ARCHITECTURE, DESIGN_SYSTEM |
| **PRD Protocol** | New feature request | Creates structured PRD → approval → backlog items |
| **Debt Protocol** | Shortcut taken | Logs to TECHNICAL_DEBT.md (halts for HIGH severity) |
| **Bug Protocol** | Bug discovered | Logs to BUGS.md (halts for P0/P1) |
| **Post-Task Protocol** | Task completed | Logs to DEV_JOURNAL.md |
| **Pre-Commit Protocol** | Ready to commit | Suggests conventional commit message |
| **Decision Protocol** | Architectural choice | Options table → recommendation → rationale |

## 📋 Key Documents

| Document | Purpose | Update Frequency |
|----------|---------|------------------|
| `DEV_JOURNAL.md` | Activity log | After every completed task |
| `TECHNICAL_DEBT.md` | Shortcut tracker | When shortcuts are taken |
| `BUGS.md` | Bug registry | When bugs are found |
| `BACKLOG.md` | Sprint planning | As work is planned/completed |
| `ARCHITECTURE.md` | System design | When infrastructure changes |

## 🛠️ Customization

See [`SETUP_TEMPLATE.md`](SETUP_TEMPLATE.md) for:
- Complete placeholder reference (~25 variables)
- File-by-file customization guide
- Verification checklist

## 💡 Philosophy

This framework is built on three principles:

1. **Documentation Driven** — Code follows the docs, not the other way around
2. **No Silent Shortcuts** — All debt and bugs are tracked, never hidden
3. **AI as Enforcer** — The AI assistant actively maintains standards, not just writes code

## 📖 Inspired By

- [Architecture Decision Records (ADR)](https://adr.github.io/)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [The Twelve-Factor App](https://12factor.net/)
- [Google's Engineering Practices](https://google.github.io/eng-practices/)

## 📄 License

MIT — Use freely, adapt as needed.
