---
name: corrlo-workspace
description: Use Corrlo MCP tools for accounts, employees, workspaces, backlog/tasks, projects, subscription usage, and CRM (companies, contacts, leads, opportunities, activities, pipeline). Use when the user asks about Corrlo work, tasks, CRM, employees, or subscription/MCP capacity.
---

## Preconditions

1. Ensure `corrlo_*` tools exist. If not, follow the `corrlo-setup` skill first.
2. Resolve the active account (`corrlo_list_accounts` → `corrlo_set_account` when needed).
3. Prefer Corrlo MCP over guessing from chat history or the web app.

## Tool map (read-oriented)

| Intent | Tools |
|--------|--------|
| Who is signed in | `corrlo_whoami` |
| Pick account | `corrlo_list_accounts`, `corrlo_set_account` |
| Plan / capacity | `corrlo_get_subscription`, `corrlo_get_mcp_usage` |
| People | `corrlo_list_employees`, `corrlo_search_employees` |
| Workspaces | `corrlo_list_workspaces`, `corrlo_get_workspace` |
| Backlog / tasks | `corrlo_search_backlog`, `corrlo_get_task` |
| Activity projects | `corrlo_list_projects` |
| Cross-search | `corrlo_quick_search` |
| CRM companies | `corrlo_crm_list_companies`, `corrlo_crm_get_companie` |
| CRM contacts | `corrlo_crm_list_contacts`, `corrlo_crm_get_contact` |
| CRM leads | `corrlo_crm_list_leads`, `corrlo_crm_get_lead` |
| CRM opportunities | `corrlo_crm_list_opportunities`, `corrlo_crm_get_opportunitie` |
| CRM activities | `corrlo_crm_list_activities`, `corrlo_crm_get_activitie` |
| Pipeline | `corrlo_crm_list_pipeline_stages` |

Note: some CRM get tools keep pluralized names from the OpenAPI path (`…_companie`, `…_opportunitie`, `…_activitie`). Call the exact tool names.

## Recommended flows

### Task / backlog question

1. `corrlo_list_workspaces` → pick `workspaceId` (ask if ambiguous).
2. `corrlo_search_backlog` with `workspaceId` (+ query/status/page as needed).
3. `corrlo_get_task` for details.

### CRM question

1. List with a query/page (`corrlo_crm_list_*`).
2. Get by id when the user needs a single record.
3. For deal context, also load `corrlo_crm_list_pipeline_stages` when stage names matter.

### “What can I see / am I over quota?”

1. `corrlo_get_subscription`
2. `corrlo_get_mcp_usage` if the user mentions MCP limits or daily capacity.

## Response style

- Lead with the answer (names, ids, counts), then short next steps.
- When listing, show human titles plus ids the user may need later.
- If a tool returns empty, say so and suggest a narrower query — do not fabricate rows.
- If the API returns 403 / capacity errors, explain that the account subscription or MCP daily limit blocked the call.

## Writes

Default Corrlo MCP deployments expose read tools only. Do not promise create/update/delete unless a write-capable tool is actually present in the session.
