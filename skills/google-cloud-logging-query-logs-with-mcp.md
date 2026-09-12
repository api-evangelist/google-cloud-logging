---
name: Query Cloud Logging from an agent over MCP
description: >-
  Connect an MCP client to Google's fully managed Cloud Logging remote MCP server and search
  logs with it, knowing exactly which capabilities the six published tools do and do not cover.
api: mcp/google-cloud-logging-mcp.yml
operations:
  - list_log_entries
  - list_log_names
  - list_buckets
  - get_bucket
  - list_views
  - get_view
generated: '2026-09-12'
method: generated
source: >-
  Grounded in the live tools/list response saved verbatim at
  mcp/google-cloud-logging-mcp-tools-list.json (probed 2026-09-12, HTTP 200) and
  https://docs.cloud.google.com/logging/docs/use-logging-mcp.
---

# Query Cloud Logging from an agent over MCP

## The server

- Endpoint: `https://logging.googleapis.com/mcp`
- Transport: HTTP. Fully managed and remote — there is nothing to install and no local process.
- Enabled automatically when the Cloud Logging API is enabled on the project.
- Generally available since 2026-04-22.

## Connect

Point the MCP client at the server URL with an OAuth 2.0 access token carrying one of
`https://www.googleapis.com/auth/logging.read`, `logging.write` or `logging.admin`. The
principal also needs `roles/mcp.toolUser` to make tool calls, plus a Logging role
(`roles/logging.admin`, or a narrower viewer role for read-only work).

`tools/list` answers without credentials, so you can enumerate the surface before authorizing;
actually calling a tool does not.

## What the six tools do

| Tool | Use it for |
|---|---|
| `list_log_entries` | The primary tool. Search entries by `filter`, `orderBy`, `resourceNames`. |
| `list_log_names` | Discover which log names exist in a project. |
| `list_buckets` / `get_bucket` | Inspect log storage and retention. |
| `list_views` / `get_view` | Inspect the views defined on a bucket. |

`list_log_entries` takes the **same Logging query-language `filter` string** as the REST API,
so a filter written for `entries.list` works verbatim here.

## The constraint that decides your design

**Every published tool is read-only** — all six carry `readOnlyHint: true`. There is no
ingestion tool, no sink/exclusion/metric mutation, no delete. An agent on this server can
investigate log data but cannot write or destroy it. If your flow needs to write entries or
change routing, it has to go to the REST or gRPC surface with its own credentials; that is a
deliberate boundary, not an oversight.

One more limit worth planning around: `list_log_entries` refuses calls that span multiple
resource projects. Query one project at a time.

## Budget the calls

`entries.list` — which backs `list_log_entries` — is capped at **60 requests per minute per
project and the cap cannot be raised**. An agent that loops over pages or retries aggressively
will exhaust it. There are no rate-limit headers to watch; you will only see HTTP 429 with
`RESOURCE_EXHAUSTED`. Narrow the `filter` and the timestamp range rather than paging harder.

## Pagination

`pageSize` / `pageToken` in, `nextPageToken` out. A non-empty `nextPageToken` with an empty
result does not mean the search ended — keep following the token.
