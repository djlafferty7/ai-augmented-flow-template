# Template Setup Guide

This guide walks you through customizing this template for your project.

## Quick Start

1. **Fork or clone this repository**
2. **Populate placeholders** using one of the methods below
3. **Set up MCP servers** — follow `docs/MCP_SETUP.md` (GitHub MCP is required)
4. **Customize** `docs/STANDARDS.md` for your tech stack
5. **Create initial GitHub Issues** for your backlog
6. **Delete this file** when done

---

## Populating the Template

### Option A: Manual Find & Replace

Use your IDE's find-and-replace (Cmd/Ctrl + Shift + H) to update all `{{PLACEHOLDER}}` values. See the Placeholder Reference section below.

### Option B: AI-Assisted Extraction (Recommended for existing specs)

If you have an existing specification document, PRD, or design doc, use AI to extract and populate:

1. **Add your source doc** to the repo:
   ```bash
   cp /path/to/your-spec.md docs/SOURCE_SPEC.md
   ```

2. **Run this prompt** with your AI assistant:
   ```
   Read docs/SOURCE_SPEC.md and use it to populate all {{PLACEHOLDER}} values 
   across this repository. For each file:
   1. Show me the proposed changes before applying
   2. Flag any placeholders where the source doc is ambiguous or missing info
   3. Suggest reasonable defaults where appropriate
   
   After populating placeholders:
   4. Create GitHub Issues for the initial backlog (epics, stories, tasks)
   5. Create GitHub Issues with `tech-debt` label if the spec mentions known shortcuts or TODOs
   6. Customize STANDARDS.md with project-specific coding conventions
   
   Start with VISION.md, then ARCHITECTURE.md, then AGENTS.md.
   ```

3. **Review the AI's fill plan** — approve, adjust, or provide missing details

4. **Delete or archive** `docs/SOURCE_SPEC.md` after extraction

### Option C: Interactive Session

If starting from scratch, work through placeholders conversationally:

```
I'm setting up this AI dev framework for a new project. Let's populate the 
placeholders together. Ask me questions to fill in VISION.md first, then 
we'll move to ARCHITECTURE.md and AGENTS.md.
```

### Tips for AI Extraction

- **Structured source docs work best** — headings, tables, bullet lists
- **AI will infer constraints** — review `BANNED_DEPENDENCIES` and `CI_RESTRICTIONS` carefully
- **Core values need thought** — these guide all future decisions, don't just accept AI suggestions
- **Tech stack is usually clear** — AI extracts these reliably from any spec

---

## Setting Up from a Spec File

The most common setup flow: you have an existing spec/PRD and want to bootstrap the entire project.

### Step-by-step:

1. **Add your spec** to `docs/SOURCE_SPEC.md`
2. **Use Option B above** to populate all placeholders
3. **Review AGENTS.md** — this is the central identity file. Ensure tech stack, core values, and approval model are correct.
4. **Configure MCP servers** — follow `docs/MCP_SETUP.md`. At minimum you need GitHub MCP.
5. **Use the PRD Architect agent** to create initial PRDs from your spec:
   ```
   @prd-architect Create a PRD from docs/SOURCE_SPEC.md for [feature name]
   ```
   The agent will interview you, review open issues, and create structured PRDs with GitHub Issues.
6. **Delete** `docs/SOURCE_SPEC.md` and `SETUP_TEMPLATE.md` when done.

---

## Placeholder Reference

Use find-and-replace (Cmd/Ctrl + Shift + H) to update all placeholders across the repository.

### Core Identifiers

| Placeholder | Description | Example |
|-------------|-------------|---------|
| `{{PROJECT_NAME}}` | Your product/project name | `"MyApp"` |
| `{{PROJECT_GOAL}}` | High-level project objective | `"Launch MVP by Q2 2026"` |
| `{{VALUE_PROPOSITION}}` | One-sentence value statement | `"An analytics platform that transforms raw data into actionable insights."` |

### Tech Stack

| Placeholder | Description | Default Example |
|-------------|-------------|-----------------|
| `{{TECH_STACK_BACKEND}}` | Backend language/framework | `"Python 3.11+ (FastAPI)"` |
| `{{TECH_STACK_FRONTEND}}` | Frontend framework | `"SvelteKit + TypeScript"` |
| `{{TECH_STACK_INFRA}}` | Infrastructure/IaC | `"Terraform + GCP"` |
| `{{TECH_STACK_DB}}` | Database(s) | `"Cloud SQL (PostgreSQL) + Firestore"` |
| `{{TECH_STACK_AI}}` | AI/ML services (optional) | `"Vertex AI"` |

### GitHub Configuration

| Placeholder | Description | Example |
|-------------|-------------|----------|
| `{{GITHUB_OWNER}}` | GitHub username or org | `"my-org"` |
| `{{GITHUB_REPO}}` | Repository name | `"my-project"` |
| `{{DEFAULT_BRANCH}}` | Default branch name | `"main"` |
| `{{DEV_BRANCH}}` | Development branch | `"dev"` |

### Deployment

| Placeholder | Description | Default Example |
|-------------|-------------|-----------------|
| `{{TARGET_PLATFORM}}` | Deployment target | `"GCP Cloud Run"` |
| `{{DEPLOY_REGION}}` | Primary region | `"us-central1"` |
| `{{PROJECT_ID}}` | Cloud project/account ID | `"my-project-prod-123"` |
| `{{CURRENT_PHASE}}` | Current project phase | `"MVP Development"` |

### Constraints

| Placeholder | Description | Example |
|-------------|-------------|---------|
| `{{BANNED_DEPENDENCIES}}` | Dependencies to avoid | `"jQuery, Moment.js"` |
| `{{PREFERRED_SERVICES}}` | Services to prioritize | `"GCP native services"` |
| `{{CI_RESTRICTIONS}}` | What can't run locally | `"Never run terraform apply locally — CI/CD only"` |
| `{{INFRA_DIR}}` | Infrastructure code directory | `"terraform"` |

### Vision / Core Values

| Placeholder | Description | Example |
|-------------|-------------|---------|
| `{{CORE_VALUE_1_NAME}}` | First guiding principle | `"Cloud Native First"` |
| `{{CORE_VALUE_1_DESCRIPTION}}` | Description | `"Use managed services. Avoid custom implementations."` |
| `{{CORE_VALUE_2_NAME}}` | Second principle | `"Zero Proprietary Debt"` |
| `{{CORE_VALUE_2_DESCRIPTION}}` | Description | `"All dependencies must be public/open-source."` |
| `{{CORE_VALUE_3_NAME}}` | Third principle | `"User Has Final Say"` |
| `{{CORE_VALUE_3_DESCRIPTION}}` | Description | `"AI proposes, humans approve. No autonomous high-risk changes."` |
| `{{VISION_VALUES}}` | Formatted core values block | See AGENTS.md |

### MCP & Tools

| Placeholder | Description | Example |
|-------------|-------------|----------|
| `{{MCP_TOOLS_TABLE}}` | Table of configured MCP servers | See AGENTS.md |

### Team & Workflow

| Placeholder | Description | Example |
|-------------|-------------|---------|
| `{{TEAM_COMPOSITION}}` | Team roles | `"Solo developer + AI agents"` |
| `{{PRIMARY_USER_DESCRIPTION}}` | Primary user persona | `"Small business owners"` |
| `{{SECONDARY_USER_DESCRIPTION}}` | Secondary user persona | `"Team administrators"` |
| `{{INSTALL_COMMAND}}` | Install dependencies | `"poetry install && cd frontend && npm install"` |
| `{{TEST_COMMAND}}` | Run tests | `"pytest && cd frontend && npm test"` |
| `{{UNIT_TEST_COMMAND}}` | Run unit tests | `"pytest tests/unit"` |
| `{{INTEGRATION_TEST_COMMAND}}` | Run integration tests | `"pytest tests/integration"` |
| `{{LICENSE_TYPE}}` | Project license | `"MIT"` |
| `{{COMMUNICATION_CHANNEL}}` | Team communication | `"GitHub Discussions"` |

---

## Files to Customize

After replacing placeholders, review these files for project-specific content:

| File | What to Customize |
|------|-------------------|
| `AGENTS.md` | Tech stack, core values, MCP tools table |
| `docs/VISION.md` | Core values, target audience details |
| `docs/ARCHITECTURE.md` | Services list, data flow, infrastructure details |
| `docs/STANDARDS.md` | Coding conventions for your specific stack |
| `docs/DESIGN_SYSTEM.md` | Color palette, typography, UI patterns |
| `docs/DATA_DICTIONARY.md` | Field names and types for your entities |
| `docs/SETUP.md` | Prerequisites, install commands, deployment steps |
| `docs/CONTRIBUTING.md` | Code standards, PR process, testing commands |
| `docs/prd/PRD-TEMPLATE.md` | Vision alignment checklist (core value names) |
| `.github/instructions/` | Tech-specific conventions for each file type |
| `.github/agents/` | Enable/disable agents for your workflow |

### Agent Configuration

| Agent | Type | Keep If... |
|-------|------|------------|
| **Bug Hunter** | User-accessible | Always useful |
| **Code Reviewer** | User-accessible | You use GitHub PRs |
| **Terraform Guardian** | User-accessible | You use Terraform for IaC |
| **PRD Architect** | User-accessible | You write PRDs for features |
| **Debt Logger** | Subagent | Always useful |
| **Decision Architect** | Subagent | You document architectural decisions |
| **RCA Worker** | Subagent | Always useful |

---

## Verification Checklist

Before starting development, verify:

- [ ] All `{{PLACEHOLDER}}` strings replaced (grep for `{{`)
- [ ] `AGENTS.md` customized with project identity and core values
- [ ] `docs/VISION.md` reflects your actual project goals
- [ ] `docs/ARCHITECTURE.md` has your services listed
- [ ] `docs/STANDARDS.md` matches your tech stack
- [ ] `docs/DESIGN_SYSTEM.md` has your brand colors (if applicable)
- [ ] MCP servers configured and tested (at minimum: GitHub)
- [ ] Initial GitHub Issues created for your backlog
- [ ] `docs/SOURCE_SPEC.md` deleted (if used for AI extraction)
- [ ] This file (`SETUP_TEMPLATE.md`) deleted
