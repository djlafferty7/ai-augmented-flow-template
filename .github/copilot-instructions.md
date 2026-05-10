# Copilot Agent Configuration

<!-- This file is Copilot-specific. Cross-agent rules live in AGENTS.md at workspace root. -->

## Shared Context

See `AGENTS.md` for project identity, tech stack, coding principles, tiered approval model, verification loop, and reference documents. Everything in AGENTS.md applies here — do not duplicate it.

---

## Specialist Agents

Switch to these specialists via the **agent dropdown** when triggered.

### User-Accessible Agents (in dropdown)
| Agent | Trigger | Description |
|-------|---------|-------------|
| **Bug Hunter** | Bug reports, errors, 500s | Systematic RCA + GitHub Issue creation with P0-P3 triage |
| **Terraform Guardian** | Infrastructure changes | Enforces IaC standards, blocks manual resource creation |
| **Code Reviewer** | PR review, review comments | Reviews PRs and addresses code review comments |
| **PRD Architect** | Feature requests, planning | Interactive PRD creation with issue/debt review |

### Subagent-Only Workers (invoked by specialists)
| Agent | Invoked By | Description |
|-------|------------|-------------|
| **RCA Worker** | Bug Hunter | Read-only root cause analysis (5 Whys methodology) |
| **Debt Logger** | Bug Hunter, any agent | Creates GitHub Issues for technical debt with severity assessment |
| **Decision Architect** | Planning tasks | Options analysis with ADR creation |

---

## Severity Quick Reference

| Level | Bugs (Priority) | Debt (Severity) | Response |
|-------|-----------------|-----------------|----------|
| **P0/CRITICAL** | System down, data loss | Security vuln, credential exposure | HALT and address immediately |
| **P1/HIGH** | Core feature broken | Architecture violation, banned dep | Same-day fix |
| **P2/MEDIUM** | Degraded feature | Missing tests, poor error handling | This sprint |
| **P3/LOW** | Minor/cosmetic | Code smell, docs gap | Backlog |

---

## The Debt Protocol (Mandatory)

Trigger this if a shortcut is taken or a best practice is skipped.

**Scenario A: Major Violation (CRITICAL/HIGH)**
1. **HALT Code Generation.**
2. Output:
   > ⚠️ **Technical Debt Halt**
   > This is a serious violation requiring acknowledgment.
   > **Proposed GitHub Issue:**
   > - **Title:** [Tech Debt] [Component]: [Short description]
   > - **Severity:** HIGH
   > - **Labels:** `tech-debt`, severity level
   > - **Description:** [What constitutes the debt]
   > - **Plan to Fix:** [Refactor Plan]
   > *Shall I create this issue and proceed?*
3. Create a GitHub Issue with `tech-debt` + severity label via MCP.

**Scenario B: Minor Shortcut (MEDIUM/LOW)**
1. Create a GitHub Issue with `tech-debt` + severity label via MCP immediately without halting.
2. Output: "ℹ️ *Created GitHub Issue #YYY for tech debt.*"

---

## The Bug Protocol (Mandatory)

Trigger when a bug is discovered during development or reported by the user.

**Scenario A: P0/P1 Bug (Critical/Major)**
1. **HALT Current Work.**
2. Output:
   > 🐛 **Bug Alert (P0/P1)**
   > A critical bug has been identified that requires immediate attention.
   > *Shall I create a GitHub Issue and investigate immediately?*
3. Create a GitHub Issue with `bug` + priority label via MCP.

**Scenario B: P2/P3 Bug (Moderate/Minor)**
1. Create a GitHub Issue with `bug` + priority label via MCP without halting.
2. Output: "🐛 *Created GitHub Issue for bug (P2/P3).*"

---

## Post-Task Protocol

After completing a coding task:
1. Ensure all tests pass (Verification Loop from AGENTS.md)
2. Update relevant GitHub Issues (close completed, comment on progress)
3. Suggest a conventional commit message (Pre-Commit Protocol from AGENTS.md)

---

## The 6-Step Consistency Check

Before generating ANY code, perform this internal audit:

1. **Vision Alignment:** Does this advance the core values? (Ref: `docs/VISION.md`)
2. **Dependency Check:** Does this use banned dependencies? (Ref: `docs/STANDARDS.md`)
3. **Visual Consistency:** Does the UI match existing patterns? (Ref: `docs/DESIGN_SYSTEM.md`)
4. **Data Consistency:** Do field names match `docs/DATA_DICTIONARY.md`?
5. **Debt Check:** Taking a shortcut? → Create GitHub Issue via Debt Protocol above
6. **Verification:** Run tests after changes (Verification Loop from AGENTS.md)

## Output Rules

- **No Silent Refactors:** Never change a core library without explicit permission.
- **Prefer Native Services:** Always prioritize {{PREFERRED_SERVICES}} over external third-party tools.
- **Infrastructure Docs Sync:** When modifying infrastructure, update `docs/ARCHITECTURE.md` (between `<!-- INFRA-START -->` and `<!-- INFRA-END -->` markers).
