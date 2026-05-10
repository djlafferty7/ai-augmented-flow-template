---
name: 'Backend Standards'
description: 'FastAPI + Python conventions and patterns'
applyTo: '**/*.py'
---

# Backend Coding Standards

Reference: `docs/STANDARDS.md` for general principles, `docs/DATA_DICTIONARY.md` for field names.

## FastAPI Conventions

- Use `async def` for all I/O-bound endpoints.
- Define request/response models with Pydantic `BaseModel`. Never accept raw dicts from API input.
- Use dependency injection (`Depends()`) for shared logic (auth, database sessions).
- Group related endpoints in routers. One router per domain (e.g., `users.py`, `orders.py`).

## Type Safety

- Type hints required on ALL function signatures — parameters and return types.
- Use Pydantic for data validation at system boundaries.
- Use `TypeAlias` for complex types. Avoid bare `dict` or `list` in signatures.

## Error Handling

- Raise `HTTPException` with appropriate status codes. Never return bare 500s.
- Use custom exception handlers for domain-specific errors.
- Log errors with Python's standard `logging` module. Include context (user_id, request_id).
- Follow Fail Fast principle: validate early, surface errors immediately.

## Testing

- Tests go in `tests/` mirroring the source structure.
- Use `pytest` with `httpx.AsyncClient` for API endpoint tests.
- Mock external services (database, APIs) — don't hit real services in unit tests.
- Name tests descriptively: `test_create_user_returns_201_with_valid_input`.

## Code Style

- Follow PEP 8. Use `ruff` for linting and formatting.
- Imports: stdlib first, third-party second, local third. Use absolute imports.
- No wildcard imports. No circular imports.
- Docstrings for public API functions only — code should be self-documenting.
