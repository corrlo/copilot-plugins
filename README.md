# Corrlo Copilot plugin marketplace (template)

GitHub Copilot / VS Code discovers Agent Plugins from a **marketplace** repo that contains `.github/plugin/marketplace.json`.

Published marketplace: **[corrlo/copilot-plugins](https://github.com/corrlo/copilot-plugins)**.  
This folder is the source template; keep `plugins/corrlo` synced with `../copilot-plugin` via:

```bash
./scripts/sync-copilot-plugin.sh
```

## Layout

```
marketplace/
  .github/plugin/marketplace.json
  plugins/corrlo/          # synced from ../copilot-plugin
    plugin.json
    mcp.json
    skills/
    com.github.copilot/
    README.md
    assets/
```

## Publish

1. Run `./scripts/sync-copilot-plugin.sh` from `corrlo-mcp/`.
2. Copy `marketplace/` to the root of `corrlo/copilot-plugins` (or push this tree).
3. Tag `v1.1.0` (immutable ref for Awesome Copilot / marketplace installs).
4. Repo must be **public**.

## User install (VS Code)

1. Settings → enable Agent Plugins if needed (`chat.plugins.enabled`).
2. Add marketplace:

```json
{
  "chat.plugins.marketplaces": [
    "corrlo/copilot-plugins"
  ]
}
```

3. Chat: Open Customizations → Plugins → Browse Marketplace → install **corrlo**.
4. Authenticate Corrlo MCP (browser consent) when prompted.
5. Use skills / **Corrlo Workspace** agent for account + task/CRM flows.

## Awesome Copilot / MCP Registry

See `../docs/COPILOT_PLUGIN_CHECKLIST.md` and `../docs/MCP_REGISTRY_PUBLISH.md`.  
Do not reopen rejected issue #6527 — open a new external plugin submission after `v1.1.0` + registry publish.

## Without marketplace

Users can still add `https://mcp.corrlo.com/mcp` via `.vscode/mcp.json` — see `../examples/vscode.mcp.json`.
