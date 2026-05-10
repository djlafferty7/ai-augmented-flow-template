# Setup Guide

> Developer environment setup and deployment instructions for {{PROJECT_NAME}}.

---

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Local Development Setup](#local-development-setup)
3. [Environment Configuration](#environment-configuration)
4. [Deployment](#deployment)
5. [Verification](#verification)
6. [Troubleshooting](#troubleshooting)

---

## Prerequisites

### Required Tools

| Tool | Version | Purpose |
|------|---------|---------|
| {{TOOL_1}} | {{VERSION_1}} | {{PURPOSE_1}} |
| {{TOOL_2}} | {{VERSION_2}} | {{PURPOSE_2}} |
| {{TOOL_3}} | {{VERSION_3}} | {{PURPOSE_3}} |

### Required Access

| Access | How to Verify |
|--------|---------------|
| {{ACCESS_1}} | {{VERIFY_COMMAND_1}} |
| {{ACCESS_2}} | {{VERIFY_COMMAND_2}} |

### Environment Information

```bash
# Set these for your environment
export PROJECT_ID="{{PROJECT_ID}}"
export REGION="{{DEPLOY_REGION}}"
export ENVIRONMENT="dev"  # dev | staging | prod
```

---

## Local Development Setup

### 1. Clone the Repository

```bash
git clone https://github.com/{{GITHUB_OWNER}}/{{GITHUB_REPO}}.git
cd {{GITHUB_REPO}}
```

### 2. Install Dependencies

```bash
# Backend
{{BACKEND_INSTALL_COMMAND}}

# Frontend (if applicable)
{{FRONTEND_INSTALL_COMMAND}}
```

### 3. Configure Local Environment

```bash
cp .env.example .env
# Edit .env with your local configuration
```

---

## Environment Configuration

### Environment Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `{{ENV_VAR_1}}` | {{ENV_VAR_1_DESC}} | `{{ENV_VAR_1_EXAMPLE}}` |
| `{{ENV_VAR_2}}` | {{ENV_VAR_2_DESC}} | `{{ENV_VAR_2_EXAMPLE}}` |

### Secrets Management

Secrets are stored in {{SECRET_MANAGER}} (e.g., GCP Secret Manager, AWS Secrets Manager, HashiCorp Vault).

```bash
# Access a secret locally (example for GCP)
gcloud secrets versions access latest --secret="{{SECRET_NAME}}"
```

---

## Deployment

### Option A: CI/CD (Recommended)

All deployments go through the CI/CD pipeline:

1. Create a branch from `{{DEV_BRANCH}}`
2. Make changes and push
3. Open a Pull Request to `{{DEFAULT_BRANCH}}`
4. CI runs tests and `terraform plan`
5. On merge, CD runs `terraform apply` and deploys services

**Monitor:** {{CI_CD_DASHBOARD_URL}}

### Option B: Bootstrap (First-Time Setup)

For initial environment setup, some resources may need manual creation:

```bash
cd {{INFRA_DIR}}/bootstrap
./bootstrap.sh $PROJECT_ID $ENVIRONMENT
```

**What bootstrap creates:**

| Resource | Purpose |
|----------|---------|
| {{BOOTSTRAP_RESOURCE_1}} | {{BOOTSTRAP_PURPOSE_1}} |
| {{BOOTSTRAP_RESOURCE_2}} | {{BOOTSTRAP_PURPOSE_2}} |

### Local Terraform (Emergency Only)

> ⚠️ **Warning:** Local `terraform apply` is discouraged. Use CI/CD.

```bash
cd {{INFRA_DIR}}/environments/$ENVIRONMENT
terraform init
terraform plan    # Review changes
# terraform apply  # Only if CI/CD is unavailable
```

---

## Verification

### Health Checks

```bash
# Check service health
curl https://{{SERVICE_URL}}/health

# Check all services
./scripts/health-check.sh
```

### Smoke Tests

```bash
# Run basic smoke tests
{{SMOKE_TEST_COMMAND}}
```

---

## Troubleshooting

### Common Issues

| Issue | Cause | Solution |
|-------|-------|----------|
| {{ISSUE_1}} | {{CAUSE_1}} | {{SOLUTION_1}} |
| {{ISSUE_2}} | {{CAUSE_2}} | {{SOLUTION_2}} |

### Logs

```bash
# View service logs (example for Cloud Run)
gcloud logging read "resource.type=cloud_run_revision" --limit=50

# View specific service
gcloud logging read "resource.labels.service_name={{SERVICE_NAME}}" --limit=50
```

### Getting Help

- Check GitHub Issues for known bugs: https://github.com/{{GITHUB_OWNER}}/{{GITHUB_REPO}}/issues?q=label%3Abug
- Search GitHub Issues labeled `tech-debt` for known limitations
- Open an issue: https://github.com/{{GITHUB_OWNER}}/{{GITHUB_REPO}}/issues

---

## Change Log

| Date | Change | Author |
|------|--------|--------|
| {{SETUP_DATE}} | Initial setup guide | {{SETUP_AUTHOR}} |
