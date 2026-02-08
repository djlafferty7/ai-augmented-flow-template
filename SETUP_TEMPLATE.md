# 🛠️ Template Setup Guide

This guide walks you through customizing this template for your project.

## Quick Start

1. **Fork or clone this repository**
2. **Find & replace all placeholders** (listed below)
3. **Customize** `DESIGN_SYSTEM.md` for your UI
4. **Review** `GUIDELINES.md` tech-specific sections
5. **Delete this file** when done

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

### Vision / Core Values

| Placeholder | Description | Example |
|-------------|-------------|---------|
| `{{CORE_VALUE_1_NAME}}` | First guiding principle name | `"Cloud Native First"` |
| `{{CORE_VALUE_1_DESCRIPTION}}` | Description | `"Use managed services. Avoid custom implementations."` |
| `{{CORE_VALUE_2_NAME}}` | Second principle name | `"Zero Proprietary Debt"` |
| `{{CORE_VALUE_2_DESCRIPTION}}` | Description | `"All dependencies must be public/open-source."` |
| `{{CORE_VALUE_3_NAME}}` | Third principle name | `"Documentation Driven"` |
| `{{CORE_VALUE_3_DESCRIPTION}}` | Description | `"Code follows the docs, not the other way around."` |

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

---

## Verification Checklist

Before starting development, verify:

- [ ] All `{{PLACEHOLDER}}` strings replaced (grep for `{{`)
- [ ] `VISION.md` reflects your actual project goals
- [ ] `ARCHITECTURE.md` has your services listed
- [ ] `GUIDELINES.md` matches your tech stack
- [ ] `DESIGN_SYSTEM.md` has your brand colors (if applicable)
- [ ] First entry added to `DEV_JOURNAL.md`
- [ ] This file (`SETUP_TEMPLATE.md`) deleted

---

## Framework Overview

This template implements an **AI-augmented development workflow** with these core protocols:

| Protocol | Purpose | Trigger |
|----------|---------|---------|
| **5-Step Consistency Check** | Validate every code change | Before any code generation |
| **PRD Protocol** | Document new features | New feature requests |
| **Debt Protocol** | Track shortcuts | Hacks or skipped best practices |
| **Bug Protocol** | Track defects | Bug discovery |
| **Post-Task Protocol** | Journal completed work | After completing any task |
| **Pre-Commit Protocol** | Standardize commits | Before git commit |
| **Decision Protocol** | Document choices | Architectural decisions |

See `.github/copilot-instructions.md` for full protocol definitions.
