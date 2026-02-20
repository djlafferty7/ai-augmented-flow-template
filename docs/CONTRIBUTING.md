# Contributing to {{PROJECT_NAME}}

Guidelines for contributing to this project.

---

## Development Setup

See [SETUP.md](SETUP.md) for environment configuration.

### Quick Start

```bash
git clone https://github.com/{{GITHUB_OWNER}}/{{GITHUB_REPO}}.git
cd {{GITHUB_REPO}}
{{INSTALL_COMMAND}}
pre-commit install
pre-commit install --hook-type commit-msg
```

---

## Commit Conventions

We use [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <description>

[optional body]

[optional footer(s)]
```

### Types

| Type | Description |
|------|-------------|
| `feat` | New feature |
| `fix` | Bug fix |
| `docs` | Documentation only |
| `style` | Formatting, no code change |
| `refactor` | Code change that neither fixes a bug nor adds a feature |
| `perf` | Performance improvement |
| `test` | Adding or updating tests |
| `build` | Build system or dependencies |
| `ci` | CI/CD configuration |
| `chore` | Other changes (e.g., updating .gitignore) |
| `revert` | Reverting a previous commit |

### Examples

```bash
feat(api): add user authentication endpoint
fix(frontend): resolve calendar sync issue
docs: update README setup instructions
refactor(database): optimize query performance
test(api): add integration tests for auth flow
```

### Scope

Scope should be the service, module, or area affected:

- `api`, `frontend`, `infra`, `docs`
- Or service names: `auth`, `payments`, `notifications`

---

## Code Standards

### General

- Write self-documenting code with clear naming
- Add comments for complex logic only
- Keep functions focused (single responsibility)
- Write tests for new functionality

### Language-Specific

<!-- Customize these sections for your tech stack -->

#### {{TECH_STACK_BACKEND}}

{{BACKEND_STANDARDS}}

#### {{TECH_STACK_FRONTEND}}

{{FRONTEND_STANDARDS}}

#### Infrastructure ({{TECH_STACK_INFRA}})

- All resources defined in `{{INFRA_DIR}}/`
- Run `terraform fmt -recursive` before committing
- Never run `terraform apply` locally — CI/CD only

See [GUIDELINES.md](GUIDELINES.md) for full coding standards.

---

## Pull Request Process

### Before Opening a PR

1. **Branch from `{{DEV_BRANCH}}`** (not `{{DEFAULT_BRANCH}}`)
2. **Run pre-commit hooks:**

   ```bash
   pre-commit run --all-files
   ```

3. **Run tests:**

   ```bash
   {{TEST_COMMAND}}
   ```

4. **Update documentation** if behavior changes

### PR Requirements

- [ ] Descriptive title using conventional commit format
- [ ] Description explains *what* and *why*
- [ ] Tests pass
- [ ] No linting errors
- [ ] Documentation updated (if applicable)
- [ ] No secrets or credentials committed

### Review Process

1. Open PR against `{{DEV_BRANCH}}`
2. Automated checks run (lint, test, terraform plan)
3. Request review from a maintainer
4. Address feedback
5. Merge when approved

---

## Testing

### Unit Tests

```bash
{{UNIT_TEST_COMMAND}}
```

### Integration Tests

```bash
{{INTEGRATION_TEST_COMMAND}}
```

### Test Coverage

Aim for meaningful coverage, not 100%. Focus on:

- Business logic
- Edge cases
- Error handling

---

## Pre-commit Hooks

We use [pre-commit](https://pre-commit.com/) to enforce standards:

### Installation

```bash
pip install pre-commit
pre-commit install
pre-commit install --hook-type commit-msg
```

### Configured Hooks

| Hook | Purpose |
|------|---------|
| `trailing-whitespace` | Remove trailing whitespace |
| `end-of-file-fixer` | Ensure files end with newline |
| `check-yaml` | Validate YAML syntax |
| `check-json` | Validate JSON syntax |
| `commitlint` | Enforce conventional commits |
| {{ADDITIONAL_HOOK}} | {{HOOK_PURPOSE}} |

### Running Manually

```bash
# Run on staged files
pre-commit run

# Run on all files
pre-commit run --all-files

# Run specific hook
pre-commit run <hook-id>
```

---

## Getting Help

- **Documentation:** Check `docs/` for guides and references
- **Bugs:** Report in `docs/BUGS.md` or open a GitHub issue
- **Questions:** {{COMMUNICATION_CHANNEL}} (e.g., Slack, Discord, GitHub Discussions)

---

## License

{{LICENSE_TYPE}}
