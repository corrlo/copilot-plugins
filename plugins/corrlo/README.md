# Corrlo — GitHub Copilot / VS Code Agent Plugin

Agent Plugins 1.0 package for **GitHub Copilot**: portable skills + Copilot agent/commands + remote Corrlo MCP.

- **MCP:** `https://mcp.corrlo.com/mcp` (`com.corrlo/mcp` in the official MCP Registry)
- **Auth:** App Connect OAuth (DCR + PKCE). Consent: `https://www.corrlo.com/oauth/app-connect/consent`
- **Version:** `1.1.0`

## What’s inside

| Component | Path | Purpose |
|-----------|------|---------|
| MCP | `mcp.json` | Hosted Streamable HTTP server |
| Skill | `skills/corrlo-setup/` | Connect / OAuth / account selection |
| Skill | `skills/corrlo-workspace/` | Tool map and task/CRM flows |
| Agent | `com.github.copilot/agents/corrlo-workspace.agent.md` | Corrlo-focused Copilot agent |
| Command | `com.github.copilot/commands/corrlo-accounts.prompt.md` | List / set Corrlo accounts |

## Install (quick — without marketplace)

1. Enable Agent Plugins if needed: `chat.plugins.enabled` = `true`.
2. Or add the server in `.vscode/mcp.json`:

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

3. Copilot Chat → Agent mode → start/auth `corrlo` → Approve on Corrlo consent.
4. Try: “List my Corrlo accounts.” or switch to the **Corrlo Workspace** agent.

Skills load on demand when you ask about Corrlo setup or workspace/CRM data.

## Marketplace

- Custom: [corrlo/copilot-plugins](https://github.com/corrlo/copilot-plugins) (`chat.plugins.marketplaces`)
- Default Awesome Copilot: submit after MCP Registry publish — see [docs/COPILOT_PLUGIN_CHECKLIST.md](../docs/COPILOT_PLUGIN_CHECKLIST.md) and [docs/MCP_REGISTRY_PUBLISH.md](../docs/MCP_REGISTRY_PUBLISH.md)
