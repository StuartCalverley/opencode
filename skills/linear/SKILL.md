---
name: linear
description: >-
  Manages Linear tickets — list, create, update, view issues. Use when the
  user says "create ticket", "Linear", "make a task", or wants to turn a plan
  into tracked work on their Linear board.
---

# Linear ticket management

Your Linear account is already connected. Use the Composio tools to manage
tickets.

## Discover context

Before creating or updating tickets, gather the IDs you need.
**IMPORTANT: Always re-fetch every call — stale/truncated IDs will fail.**

Add entries above as new projects are onboarded. These skip the team-list step.

- **Teams** — `LINEAR_LIST_LINEAR_TEAMS` (call fresh for unlisted projects)
- **Projects** — `LINEAR_LIST_LINEAR_PROJECTS`
- **Workflow states** — `LINEAR_LIST_LINEAR_STATES` (requires `team_id`)
- **Labels** — `LINEAR_LIST_LINEAR_LABELS` (scope by `team_id` for leaf labels)
- **Users** — `LINEAR_LIST_LINEAR_USERS` or `LINEAR_GET_CURRENT_USER`

## View issues

### Quick check (titles only) — TOKEN EFFICIENT

For checking if a ticket exists or getting a quick overview, use a minimal
GraphQL query to fetch only essential fields. This returns ~80-90% less data
than the full listing.

```graphql
query {
  issues(first: 50) {
    nodes {
      id
      identifier
      title
      state {
        name
      }
    }
    pageInfo {
      hasNextPage
      endCursor
    }
  }
}
```

**Use via:** `LINEAR_RUN_QUERY_OR_MUTATION` with the query above.

**Returns:** id, identifier (e.g., "STU-23"), title, state name, pagination

### Full details — WHEN NEEDED

Use these when you need complete ticket information (descriptions, assignees,
labels, etc.):

- **List** — `LINEAR_LIST_LINEAR_ISSUES` (paginate with `after`/`endCursor`, max 250 per page)
  - ⚠️ **High token usage** — returns full descriptions, nested team/project/label objects, timestamps
  - Only use when you need the full payload
  
- **Detail** — `LINEAR_GET_LINEAR_ISSUE` for full issue info

### When to use which

| Use case | Tool | Reason |
|----------|------|--------|
| Check if ticket exists | `LINEAR_RUN_QUERY_OR_MUTATION` with minimal query | Low tokens, just need titles |
| Get ticket count/overview | `LINEAR_RUN_QUERY_OR_MUTATION` with minimal query | Low tokens, fast scan |
| Search by title keywords | `LINEAR_RUN_QUERY_OR_MUTATION` with minimal query | Filter client-side after fetch |
| Create ticket (need to check duplicates) | `LINEAR_RUN_QUERY_OR_MUTATION` with minimal query | Just need to compare titles |
| Read full ticket details | `LINEAR_GET_LINEAR_ISSUE` | Complete data for one ticket |
| Export/reporting | `LINEAR_LIST_LINEAR_ISSUES` | Full data needed |

## Create a ticket

Required: `team_id`, `title`. All UUIDs must belong to the same team.

`LINEAR_CREATE_LINEAR_ISSUE` — see its schema for optional fields (priority,
assignee, state, project, labels, description, due date, estimate, cycle).

**Description style**: State the **problem** plus **desired outcome** only.
Do not include implementation details or technical solutions.

## Update a ticket

`LINEAR_UPDATE_ISSUE` — only include fields you want to change.

## Workflow

1. **Session setup** — Pass `session: {generate_id: true}` to `COMPOSIO_SEARCH_TOOLS` for a new workflow, or `session: {id}` to continue existing. Use the returned `session_id` in all subsequent meta tool calls.
2. **Discover context** — Fetch fresh teams, projects, states, labels, and users via the list tools above. Never reuse stale IDs. **Shortcut:** If the project is in the Cached IDs table above, use the stored `team_id` and skip `LINEAR_LIST_LINEAR_TEAMS`.
3. **Check for existing tickets** — Use `LINEAR_RUN_QUERY_OR_MUTATION` with minimal query (titles only) to check if similar tickets already exist.
4. **Confirm** — Present findings to the user before creating or updating.
5. **Write description** — Problem + desired outcome only. No implementation details.
6. **Execute** — Create or update via `LINEAR_CREATE_LINEAR_ISSUE` / `LINEAR_UPDATE_ISSUE`.
7. **Verify** — Confirm the result (show ticket URL to the user).
