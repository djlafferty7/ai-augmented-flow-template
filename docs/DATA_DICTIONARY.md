# Data Dictionary

> Canonical field names, types, and descriptions for all data entities in the {{PROJECT_NAME}} platform.

## Purpose

This document serves as the single source of truth for:
- Field naming conventions across all services
- Data types and validation rules
- Enum values and their meanings
- Cross-service data consistency

**The 6-Step Consistency Protocol requires checking this document before defining any new data fields.**

---

## Naming Conventions

| Convention | Rule | Example |
|------------|------|---------|
| Field names | `snake_case` | `created_at`, `user_id` |
| Enum values | `SCREAMING_SNAKE_CASE` | `PENDING`, `IN_PROGRESS` |
| Boolean fields | Prefix with `is_`, `has_`, `can_` | `is_active`, `has_verified` |
| Timestamps | Suffix with `_at` | `created_at`, `updated_at` |
| Foreign keys | Suffix with `_id` | `user_id`, `order_id` |

---

## Core Entities

### User
| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `id` | string (UUID) | Yes | Unique identifier |
| `email` | string | Yes | User's email address |
| `display_name` | string | No | User's display name |
| `created_at` | timestamp | Yes | Account creation time |
| `updated_at` | timestamp | Yes | Last modification time |
| `is_active` | boolean | Yes | Whether account is active |

<!-- Add more entities as your project grows -->

---

## Enums

### Status Values
| Value | Description |
|-------|-------------|
| `PENDING` | Awaiting processing |
| `IN_PROGRESS` | Currently being processed |
| `COMPLETED` | Successfully finished |
| `FAILED` | Processing failed |
| `CANCELLED` | Cancelled by user or system |

<!-- Add more enums as your project grows -->

---

## API Field Mapping

When field names differ between layers, document the mapping:

| API Field | Database Field | Notes |
|-----------|----------------|-------|
| `userId` | `user_id` | API uses camelCase |
| `createdAt` | `created_at` | ISO 8601 format in API |

---

## Validation Rules

| Field Type | Rule |
|------------|------|
| Email | RFC 5322 compliant |
| UUID | Version 4, lowercase |
| Timestamps | ISO 8601 with timezone |
| Phone | E.164 format |

---

## Change Log

| Date | Change | Author |
|------|--------|--------|
| {{SETUP_DATE}} | Initial data dictionary | {{SETUP_AUTHOR}} |
