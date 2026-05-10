---
name: 'Testing Standards'
description: 'Test-first development and verification loop'
applyTo: '**/*test*,**/*spec*'
---

# Testing Standards

Reference: `docs/STANDARDS.md` for general principles (especially Test-First Development and Verification Loop).

## Test-First Workflow

1. **Write a failing test** that describes the expected behavior
2. **Run it** — confirm it fails for the right reason
3. **Implement** the minimum code to make it pass
4. **Run again** — confirm it passes
5. **Refactor** if needed, re-run to confirm still green

This applies to bug fixes too: reproduce the bug with a test first.

## What to Test

Focus on:
- **Business logic** — the core domain rules
- **Edge cases** — boundary values, empty inputs, nulls
- **Error handling** — expected failures produce correct errors
- **API contracts** — endpoints return expected status codes and shapes

Skip:
- Testing framework internals or third-party library behavior
- Pure pass-through functions with no logic
- CSS or visual layout (use visual regression tools instead)

## Naming

Name tests descriptively so failures are self-documenting:
- `test_create_user_returns_201_with_valid_input`
- `test_delete_order_returns_403_when_unauthorized`
- Not: `test_1`, `test_create`, `test_happy_path`

## Structure

- Mirror the source directory structure in `tests/`.
- Separate unit tests from integration tests (`tests/unit/`, `tests/integration/`).
- Use fixtures for shared setup. Avoid test interdependencies.

## Verification Loop

After writing or modifying tests, always run them in the terminal to confirm results. Never declare tests complete without executing them.
