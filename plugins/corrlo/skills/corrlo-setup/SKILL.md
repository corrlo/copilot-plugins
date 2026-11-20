---
name: corrlo-setup
description: First-time Corrlo MCP setup in GitHub Copilot / VS Code. Use when Corrlo tools are missing, OAuth/consent fails, the user asks to connect Corrlo, or before any Corrlo account/workspace/task/CRM request if corrlo_* tools are not available.
---

## Corrlo MCP server

The MCP server id is `corrlo`. Prefer tools from this server for Corrlo data. Do not invent REST calls or ask the user to open the Corrlo web UI first when MCP can answer.

Production endpoint (already in this plugin’s `mcp.json`):

`https://mcp.corrlo.com/mcp`

Auth is Corrlo App Connect OAuth (DCR + PKCE). Consent UI: `https://www.corrlo.com/oauth/app-connect/consent`.

## When tools are missing

If `corrlo_*` tools are not in the tool list:

1. Tell the user the Corrlo MCP server must be started and authenticated.
2. Give surface-specific steps (do not invent product UI labels beyond these):

**VS Code / Copilot Chat**

1. Open Command Palette.
2. Run **MCP: List Servers**.
3. Select `corrlo` → **Start Server** (or Restart).
4. Complete browser sign-in and **Approve** on the Corrlo consent page.
5. Confirm tools appear, then continue the original request.

**Copilot CLI** (if applicable): reload MCP / re-auth for the `corrlo` server, then retry.

3. After auth, run `corrlo_whoami` once. If it fails, stop and report the error briefly; do not suggest scraping Corrlo in a browser as a substitute.

## Account selection (required when multiple memberships)

1. Call `corrlo_list_accounts`.
2. If more than one membership exists, ask which account to use (title + accountId).
3. Call `corrlo_set_account` with that `accountId` before other tools.
4. Pass `accountId` on later tools when the session might reset.

## Smoke checks after setup

In order:

1. `corrlo_whoami`
2. `corrlo_list_accounts` (and `corrlo_set_account` if needed)
3. `corrlo_get_subscription` (optional capacity check)
4. Then continue with the user’s task using `corrlo-workspace` guidance

## Do not

- Store or ask for PATs when OAuth is available.
- Enable or assume write tools (writes require an explicit server flag; default tools are read-oriented).
- Guess `accountId`; always list memberships first when unclear.
