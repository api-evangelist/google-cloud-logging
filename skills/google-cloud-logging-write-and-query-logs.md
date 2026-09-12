---
name: Write and query Cloud Logging entries
description: >-
  Ingest a structured log entry into Google Cloud Logging and read it back with a Logging
  query-language filter, handling the pagination and error semantics this API actually uses.
api: openapi/google-cloud-logging-entries-write-api-openapi.yml
operations:
  - writeLogEntries
  - listLogEntries
generated: '2026-09-12'
method: generated
source: >-
  Grounded in the operationIds present in openapi/, plus
  conventions/google-cloud-logging-conventions.yml and
  errors/google-cloud-logging-problem-types.yml.
---

# Write and query Cloud Logging entries

## Before you start

- Base URL: `https://logging.googleapis.com`.
- Authenticate with an OAuth 2.0 bearer token. Writing needs
  `https://www.googleapis.com/auth/logging.write`; reading needs
  `https://www.googleapis.com/auth/logging.read`. `cloud-platform` covers both.
- The IAM principal also needs the matching permission (`logging.logEntries.create`,
  `logging.logEntries.list`) on the project. A valid token with the wrong role returns 403
  `PERMISSION_DENIED`, not 401.

## 1. Write the entry — `writeLogEntries`

`POST /v2/entries:write`

Send `entries[]`, each with `logName` (`projects/PROJECT_ID/logs/LOG_ID`), a `resource`
(`{"type": "global"}` is the simplest valid one), a `severity`, and exactly one payload field —
`textPayload`, `jsonPayload` or `protoPayload`.

**Set `insertId` yourself.** It is the only replay protection this API has. If the call times
out and you retry, re-send the identical `logName` + `timestamp` + `insertId` so the duplicate
collapses. Be honest about the limit: Google de-duplicates at read time within a single query
result and explicitly disclaims de-duplication for exported logs, so `insertId` reduces
duplicate noise — it does not guarantee exactly-once ingestion.

Hard limits: 256 KiB per entry (512 KiB for audit entries), 10 MB per request, 64 labels per
entry. Exceeding any of these is a 400 `INVALID_ARGUMENT`; do not retry unchanged.

## 2. Read it back — `listLogEntries`

`POST /v2/entries:list`

Send `resourceNames` (for example `["projects/PROJECT_ID"]`) and a `filter` in the Logging
query language, for example:

```
logName="projects/PROJECT_ID/logs/LOG_ID" AND severity>=WARNING AND timestamp>="2026-09-12T00:00:00Z"
```

Set `orderBy` to `"timestamp desc"` when you want recent entries — the default
`"timestamp asc"` can be slow. Keep the filter under 20,000 characters.

Ingestion is not synchronous. An entry written a moment ago may not appear on the first read;
retry the query rather than treating an empty result as a failed write.

## 3. Page correctly

Follow `nextPageToken` into `pageToken`. **A non-empty `nextPageToken` with an empty `entries`
array does not mean the result set ended** — it means the search has not finished scanning.
Stop only when `nextPageToken` is absent.

## 4. Handle errors on `error.status`, not on text

Errors come back as `{"error": {"code", "message", "status", "details"}}` — the Google
`google.rpc.Status` envelope, not RFC 9457 problem+json. Branch on `error.status` and on
`details[].reason` with `details[].domain == "logging.googleapis.com"`.

- `RESOURCE_EXHAUSTED` (429) — you hit a quota. `entries.list` is capped at **60 requests per
  minute per project and cannot be raised**, so an agent polling logs must budget against that
  number. There are no rate-limit response headers to read; back off exponentially.
- `UNAVAILABLE` (503), `INTERNAL` (500), `DEADLINE_EXCEEDED` (504) — retry with backoff and
  jitter; honour `google.rpc.RetryInfo` when present.
- `INVALID_ARGUMENT` (400), `PERMISSION_DENIED` (403), `NOT_FOUND` (404) — fix the request or
  the grant; retrying unchanged will not help.

## What you cannot undo

There is no delete-one-entry operation. `gcloud logging logs delete` / `logs.delete` removes
every entry under a log name and is irreversible. Entries otherwise age out on the bucket's
retention period.
