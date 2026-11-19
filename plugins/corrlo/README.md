# Corrlo — GitHub Copilot / VS Code Agent Plugin

Remote MCP plugin for **GitHub Copilot** (VS Code Agent Plugins 1.0) and compatible clients.

- **MCP:** `https://mcp.corrlo.com/mcp`
- **Auth:** App Connect OAuth (DCR + PKCE). Consent: `https://www.corrlo.com/oauth/app-connect/consent`

## Install (quick — without marketplace)

1. Enable Agent Plugins in VS Code: `chat.plugins.enabled` = `true` (if prompted).
2. Or add the server directly in `.vscode/mcp.json` / user MCP config:

```json
{
  "servers": {
    "corrlo": {
      "type": "http",
      "url": "https://mcp.corrlo.com/mcp"
    }
  }
}
```

3. Copilot Chat → Agent mode → start/auth the `corrlo` MCP server → Approve on Corrlo consent.
4. Try: “List my Corrlo accounts.”

See [docs/COPILOT_PLUGIN_CHECKLIST.md](../docs/COPILOT_PLUGIN_CHECKLIST.md).

## Marketplace distribution

Host this folder from a GitHub marketplace repo (see `marketplace/` template and checklist). Users add the marketplace, then Install **corrlo**.
