---
description: "List Corrlo account memberships and set the active account if needed"
---

Using Corrlo MCP tools:

1. Call `corrlo_list_accounts`.
2. Summarize each membership (title, accountId, roles).
3. If more than one membership exists, ask which account to use, then call `corrlo_set_account`.
4. Call `corrlo_whoami` for the active context and confirm.
