# MCP Server Setup Guide

This project uses [Model Context Protocol (MCP)](https://modelcontextprotocol.io/) to give AI agents access to external tools and services. MCP servers are configured per-user — they are **not** committed to the repository.

---

## Required MCP Servers

### GitHub

Gives agents access to issues, PRs, code search, and repository management.

**Install:** Available as a built-in VS Code MCP server or via the [GitHub MCP Server](https://github.com/github/github-mcp-server).

**Used by:** Bug Hunter (issue creation), PRD Architect (issue search/creation), Code Reviewer (PR access), Debt Logger (issue creation)

### Chrome DevTools

Gives agents access to browser debugging — screenshots, console, network, DOM inspection.

**Install:** Search "Chrome DevTools MCP" in the VS Code MCP marketplace or install from [chrome-devtools-mcp](https://github.com/anthropics/anthropic-quickstarts).

**Used by:** Bug Hunter (frontend debugging), RCA Worker (visual evidence)

---

## Recommended MCP Servers (GCP)

<!-- These are optional but recommended if you're deploying to Google Cloud Platform -->

### Google Cloud MCP

Gives agents access to GCP services — Cloud Run, BigQuery, Firebase, IAM, etc.

**Install:** See [Google Cloud MCP documentation](https://cloud.google.com/products/mcp) for the latest setup instructions.

**Used by:** Terraform Guardian (infrastructure validation), general development

### BigQuery MCP

Direct access to BigQuery for data exploration and query execution.

**Install:** Available via Google Cloud MCP or as a standalone MCP server.

### Firebase MCP

Access to Firestore, Firebase Auth, and other Firebase services.

**Install:** Available via Google Cloud MCP or as a standalone MCP server.

---

## Configuration

### VS Code Settings (Recommended)

Add MCP servers in your VS Code settings (`settings.json`):

```json
{
  "mcp": {
    "servers": {
      "github": {
        "command": "npx",
        "args": ["-y", "@modelcontextprotocol/server-github"],
        "env": {
          "GITHUB_PERSONAL_ACCESS_TOKEN": "${env:GITHUB_TOKEN}"
        }
      }
    }
  }
}
```

### Workspace Configuration (Alternative)

Create a `.vscode/mcp.json` file (add to `.gitignore` to avoid committing tokens):

```json
{
  "servers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "${env:GITHUB_TOKEN}"
      }
    }
  }
}
```

---

## Verification

After configuring MCP servers:

1. Open VS Code and start a chat session
2. Type `/mcp` or check the MCP status in the chat view
3. Verify each server shows as connected
4. Test with a simple command: "List open GitHub issues"

## Security Notes

- **Never commit API tokens** to the repository
- Use environment variables (`${env:VAR_NAME}`) for sensitive values
- Review MCP server permissions — grant minimum required access
- See [VS Code MCP documentation](https://code.visualstudio.com/docs/copilot/customization/mcp-servers) for security best practices
