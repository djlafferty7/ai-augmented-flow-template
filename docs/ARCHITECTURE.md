# System Architecture

## Tech Stack

<!-- Customize to your project -->

- **Frontend:** {{TECH_STACK_FRONTEND}}
- **Backend:** {{TECH_STACK_BACKEND}}
- **Database:** {{TECH_STACK_DB}}
- **AI/ML:** {{TECH_STACK_AI}} *(if applicable)*
- **Infrastructure:** {{TECH_STACK_INFRA}}

## Services Overview

<!-- List your microservices or modules -->

| Service | Description | Port | Status |
|---------|-------------|------|--------|
| `example-service` | Example service description | 8080 | Planned |

## Banned Dependencies

*See `STANDARDS.md` for the full dependency constraints. Key bans:*

<!-- Customize based on your constraints -->

1.  **{{BANNED_DEP_1}}** — {{BANNED_DEP_1_REASON}}
2.  **{{BANNED_DEP_2}}** — {{BANNED_DEP_2_REASON}}

## Data Flow

<!-- Describe your high-level data flow -->

```
[Data Source] → [Processing] → [Storage] → [API] → [Frontend]
```

## Infrastructure (Dev Environment)

<!-- INFRA-START -->
*Last updated: YYYY-MM-DD | Source: [your IaC location]*

### Cloud Project / Account

| Setting | Value |
|---------|-------|
| Project/Account ID | `{{PROJECT_ID}}` |
| Region | `{{DEPLOY_REGION}}` |

### Networking

| Resource | Name | Configuration |
|----------|------|---------------|
| VPC | `{{PROJECT_NAME}}-vpc-dev` | *Add details* |

### Database

| Setting | Value |
|---------|-------|
| Type | {{TECH_STACK_DB}} |
| Instance | `{{PROJECT_NAME}}-db-dev` |

### Secrets

| Secret ID | Purpose |
|-----------|---------|
| `{{PROJECT_NAME}}-db-password-dev` | Database password |

### Service Accounts / IAM

| Account | Roles |
|---------|-------|
| Default Compute SA | *List roles* |

<!-- INFRA-END -->

## API Reference

<!-- Document your API endpoints -->

### Service: `example-service`

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/v1/health` | Health check |

## Cache Patterns

<!-- Document caching strategy if applicable -->

| Cache Key Pattern | TTL | Purpose |
|-------------------|-----|---------|
| `session:{user_id}` | 30m | User session |
