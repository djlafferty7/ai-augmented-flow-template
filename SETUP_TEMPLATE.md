# 🛠️ Template Setup Guide

This guide walks you through customizing this template for your project.

## Quick Start

1. **Fork or clone this repository**
2. **Populate placeholders** using one of the methods below
3. **Customize** `DESIGN_SYSTEM.md` for your UI
4. **Review** `GUIDELINES.md` tech-specific sections
5. **Delete this file** when done

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
   
   Start with VISION.md, then ARCHITECTURE.md, then copilot-instructions.md.
   ```

3. **Review the AI's fill plan** — approve, adjust, or provide missing details

4. **Delete or archive** `docs/SOURCE_SPEC.md` after extraction

### Option C: Interactive Session

If starting from scratch, work through placeholders conversationally:

```
I'm setting up this AI dev framework for a new project. Let's populate the 
placeholders together. Ask me questions to fill in VISION.md first, then 
we'll move to ARCHITECTURE.md.
```

### Tips for AI Extraction

- **Structured source docs work best** — headings, tables, bullet lists
- **AI will infer constraints** — review `BANNED_DEPENDENCIES` and `CI_RESTRICTIONS` carefully
- **Core values need thought** — these guide all future decisions, don't just accept AI suggestions
- **Tech stack is usually clear** — AI extracts these reliably from any spec

---

## Placeholder Reference

Use find-and-replace (Cmd/Ctrl + Shift + H) to update all placeholders across the repository.

### Core Identifiers

| Placeholder | Description | Example |
|-------------|-------------|---------|
| `{{PROJECT_NAME}}` | Your product/project name | `"MyApp"`, `"DataPipeline"` |
| `{{PROJECT_GOAL}}` | High-level project objective | `"Launch MVP by Q2 2026"` |
| `{{VALUE_PROPOSITION}}` | One-sentence value statement | `"An analytics platform that transforms raw data into actionable insights."` |

### Tech Stack

| Placeholder | Description | Example |
|-------------|-------------|---------|
| `{{TECH_STACK_BACKEND}}` | Backend language/framework | `"Python 3.11+ (FastAPI)"`, `"Node.js 20+ (Express)"` |
| `{{TECH_STACK_FRONTEND}}` | Frontend framework | `"React 18 + TypeScript"`, `"Vue 3 + Nuxt"` |
| `{{TECH_STACK_INFRA}}` | Infrastructure/IaC | `"AWS CDK"`, `"Terraform + GCP"`, `"Pulumi + Azure"` |
| `{{TECH_STACK_DB}}` | Database(s) | `"PostgreSQL 15 + Redis"`, `"MongoDB Atlas"` |
| `{{TECH_STACK_AI}}` | AI/ML services (optional) | `"OpenAI API"`, `"AWS Bedrock"`, `"Vertex AI"` |

### GitHub Configuration

| Placeholder | Description | Example |
|-------------|-------------|----------|
| `{{GITHUB_OWNER}}` | GitHub username or org | `"my-org"`, `"jsmith"` |
| `{{GITHUB_REPO}}` | Repository name | `"my-project"` |
| `{{DEFAULT_BRANCH}}` | Default branch name | `"main"` |
| `{{DEV_BRANCH}}` | Development branch | `"dev"`, `"develop"` |

### Deployment

| Placeholder | Description | Example |
|-------------|-------------|---------|
| `{{TARGET_PLATFORM}}` | Deployment target | `"AWS ECS"`, `"GCP Cloud Run"`, `"Vercel"` |
| `{{DEPLOY_REGION}}` | Primary region | `"us-east-1"`, `"europe-west2"` |
| `{{PROJECT_ID}}` | Cloud project/account ID | `"my-project-prod-123"` |
| `{{CURRENT_PHASE}}` | Current project phase | `"MVP Development"`, `"Phase 2: Scale"` |

### Constraints

| Placeholder | Description | Example |
|-------------|-------------|---------|
| `{{BANNED_DEPENDENCIES}}` | Dependencies to avoid | `"jQuery, Moment.js"`, `"internal-corp-lib"` |
| `{{BANNED_DEP_1}}` | First banned dependency | `"legacy-auth-lib"` |
| `{{BANNED_DEP_1_REASON}}` | Why it's banned | `"Deprecated, use OAuth2 standard"` |
| `{{BANNED_DEP_2}}` | Second banned dependency | `"proprietary-logger"` |
| `{{BANNED_DEP_2_REASON}}` | Why it's banned | `"Replace with OpenTelemetry"` |
| `{{PREFERRED_SERVICES}}` | Services to prioritize | `"AWS managed services"`, `"GCP native services"` |
| `{{CI_RESTRICTIONS}}` | What can't run locally | `"Never run terraform apply locally — CI/CD only"` |
| `{{INFRA_DIR}}` | Infrastructure code directory | `"infra"`, `"terraform"`, `"infrastructure"` |

### Vision / Core Values

| Placeholder | Description | Example |
|-------------|-------------|---------|
| `{{CORE_VALUE_1_NAME}}` | First guiding principle name | `"Cloud Native First"` |
| `{{CORE_VALUE_1_DESCRIPTION}}` | Description | `"Use managed services. Avoid custom implementations."` |
| `{{CORE_VALUE_2_NAME}}` | Second principle name | `"Zero Proprietary Debt"` |
| `{{CORE_VALUE_2_DESCRIPTION}}` | Description | `"All dependencies must be public/open-source."` |
| `{{CORE_VALUE_3_NAME}}` | Third principle name | `"Documentation Driven"` |
| `{{CORE_VALUE_3_DESCRIPTION}}` | Description | `"Code follows the docs, not the other way around."` |
| `{{VISION_VALUES}}` | Formatted core values block | See example below |

**`{{VISION_VALUES}}` Example Format:**
```markdown
- **{{CORE_VALUE_1_NAME}}:** {{CORE_VALUE_1_DESCRIPTION}}
- **{{CORE_VALUE_2_NAME}}:** {{CORE_VALUE_2_DESCRIPTION}}
- **{{CORE_VALUE_3_NAME}}:** {{CORE_VALUE_3_DESCRIPTION}}
```

### MCP Tools Configuration

| Placeholder | Description | Example |
|-------------|-------------|----------|
| `{{MCP_TOOLS_TABLE}}` | Table of available MCP servers/tools | See example below |

**`{{MCP_TOOLS_TABLE}}` Example Format:**
```markdown
| Server | Tools | Used By |
|--------|-------|---------|
| **Chrome DevTools** | Screenshots, console, network, DOM | Bug Hunter, RCA Worker |
| **GitHub** | PRs, issues, code search | Bug Hunter, Code Reviewer, PRD Architect |
```

If you don't use MCP tools, replace with: `*No MCP tools configured.*`

### Team

| Placeholder | Description | Example |
|-------------|-------------|---------|
| `{{TEAM_COMPOSITION}}` | Team roles | `"Tech Lead, 2 Engineers, 1 Designer"` |
| `{{PRIMARY_USER_DESCRIPTION}}` | Primary user persona | `"DevOps engineers managing infrastructure"` |
| `{{SECONDARY_USER_DESCRIPTION}}` | Secondary user persona | `"Business analysts viewing dashboards"` |

---

## Files to Customize

After replacing placeholders, review these files for project-specific content:

| File | What to Customize |
|------|-------------------|
| `docs/VISION.md` | Core values, target audience details |
| `docs/ARCHITECTURE.md` | Services list, data flow, infrastructure details |
| `docs/GUIDELINES.md` | Coding standards for your specific stack |
| `docs/DESIGN_SYSTEM.md` | Color palette, typography, UI patterns |
| `docs/BACKLOG.md` | Your actual epics and stories |
| `docs/prd/PRD-TEMPLATE.md` | Vision alignment checklist (core value names) |
| `docs/DATA_DICTIONARY.md` | Field names and types for your entities |
| `.github/agents/` | Enable/disable agents for your workflow |

### Agent Configuration

The template includes 7 specialist agents in `.github/agents/`. Review and customize:

| Agent | Keep If... | Remove If... |
|-------|------------|---------------|
| **Bug Hunter** | You want structured bug investigation | N/A (always useful) |
| **Code Reviewer** | You use GitHub PRs for review | No code review workflow |
| **Terraform Guardian** | Using Terraform for IaC | Different IaC tool (adapt or remove) |
| **Debt Logger** | You track technical debt | N/A (always useful) |
| **Decision Architect** | You document architectural decisions | No ADR practice |
| **PRD Architect** | You write PRDs for features | No PRD workflow |
| **RCA Worker** | You do root cause analysis | N/A (always useful) |

---

## Verification Checklist

Before starting development, verify:

- [ ] All `{{PLACEHOLDER}}` strings replaced (grep for `{{`)
- [ ] `VISION.md` reflects your actual project goals
- [ ] `ARCHITECTURE.md` has your services listed
- [ ] `GUIDELINES.md` matches your tech stack
- [ ] `DESIGN_SYSTEM.md` has your brand colors (if applicable)
- [ ] `docs/SOURCE_SPEC.md` deleted (if used for AI extraction)
- [ ] First entry added to `DEV_JOURNAL.md`
- [ ] This file (`SETUP_TEMPLATE.md`) deleted

---

## Framework Overview

This template implements an **AI-augmented development workflow** with these core protocols:

| Protocol | Purpose | Trigger |
|----------|---------|---------|
| **6-Step Consistency Check** | Validate every code change | Before any code generation |
| **PRD Protocol** | Document new features | New feature requests |
| **Debt Protocol** | Track shortcuts | Hacks or skipped best practices |
| **Bug Protocol** | Track defects | Bug discovery |
| **Post-Task Protocol** | Journal completed work | After completing any task |
| **Pre-Commit Protocol** | Standardize commits | Before git commit |
| **Decision Protocol** | Document choices | Architectural decisions |

See `.github/copilot-instructions.md` for full protocol definitions.
