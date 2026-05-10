---
name: 'Terraform Standards'
description: 'Infrastructure-as-Code conventions for Terraform + GCP'
applyTo: '**/*.tf'
---

# Terraform Coding Standards

Reference: `docs/STANDARDS.md` for general principles, `docs/ARCHITECTURE.md` for infrastructure details.

## Core Rule

**If it doesn't exist as code, it doesn't exist.** Never create cloud resources via CLI or console if Terraform can manage them.

## Module Structure

All resources defined in `{{INFRA_DIR}}/modules/`:

| Resource Type | Module Location |
|--------------|-----------------|
| Compute (Cloud Run) | `{{INFRA_DIR}}/modules/compute/` |
| IAM / Permissions | `{{INFRA_DIR}}/modules/iam/` |
| CI/CD | `{{INFRA_DIR}}/modules/cicd/` |
| Database | `{{INFRA_DIR}}/modules/database/` |
| Secrets | `{{INFRA_DIR}}/modules/secrets/` |
| Messaging / Pub/Sub | `{{INFRA_DIR}}/modules/messaging/` |
| Scheduled Jobs | `{{INFRA_DIR}}/modules/scheduler/` |

## Conventions

- Run `terraform fmt -recursive` before committing.
- Use `terraform validate` to catch syntax errors early.
- Variables go in `variables.tf`, outputs in `outputs.tf`.
- Use meaningful resource names that match the project naming convention.
- Tag all resources with `project`, `environment`, and `managed-by = "terraform"`.

## CI/CD Enforcement

- {{CI_RESTRICTIONS}}
- `terraform plan` runs on PR. `terraform apply` runs on merge to `{{DEFAULT_BRANCH}}`.
- Changes to infrastructure require user approval (HIGH-RISK per tiered autonomy model).

## Documentation Sync

After any infrastructure change, update `docs/ARCHITECTURE.md` between the `<!-- INFRA-START -->` and `<!-- INFRA-END -->` markers.
