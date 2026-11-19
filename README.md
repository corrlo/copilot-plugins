# Corrlo Copilot plugins marketplace

GitHub Copilot / VS Code Agent Plugins marketplace for **Corrlo**.

- Marketplace id: `corrlo-copilot-plugins`
- Plugin: **corrlo** → remote MCP `https://mcp.corrlo.com/mcp` (App Connect OAuth)

## Install in VS Code

```json
{
  "chat.plugins.enabled": true,
  "chat.plugins.marketplaces": [
    "corrlo/copilot-plugins"
  ]
}
```

Replace `corrlo/copilot-plugins` with this repository (`corrlo/copilot-plugins`).

Then: **Chat: Open Customizations** → Plugins → Browse Marketplace → Install **corrlo** → complete Corrlo OAuth consent.

## Manual MCP (without this marketplace)

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

## Layout

```
.github/plugin/marketplace.json
plugins/corrlo/
  plugin.json
  mcp.json
  README.md
  assets/
```
