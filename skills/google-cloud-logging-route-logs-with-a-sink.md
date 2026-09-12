---
name: Route logs to a destination with a Log Router sink
description: >-
  Create a Cloud Logging sink that routes matching entries to a destination, grant the sink's
  writer identity, and verify routing — including the permission step that is the usual cause
  of a silently non-functional sink.
api: openapi/google-cloud-logging-sinks-api-openapi.yml
operations:
  - createSink
  - listSinks
generated: '2026-09-12'
method: generated
source: >-
  Grounded in the operationIds present in openapi/, plus
  data-model/google-cloud-logging-data-model.yml and
  conventions/google-cloud-logging-conventions.yml.
---

# Route logs to a destination with a Log Router sink

## Before you start

- Needs `https://www.googleapis.com/auth/logging.admin` (or `cloud-platform`) and the
  `logging.sinks.create` permission on the container.
- Decide the container first — a sink lives on a project, folder, organization or billing
  account, and the resource name differs accordingly.

## 1. Check what already routes — `listSinks`

`GET /v2/{parent}/sinks` with `parent` such as `projects/PROJECT_ID`.

Do this before creating. Sink creation carries **no idempotency key**, so a blind retry after
an ambiguous timeout either creates a second sink or returns 409 `ALREADY_EXISTS` — and the
409 is indistinguishable from a create that genuinely succeeded. Reading first is how you tell
the two apart.

## 2. Create the sink — `createSink`

`POST /v2/{parent}/sinks`

Body fields that matter:

- `name` — unique within the container.
- `destination` — one of
  `logging.googleapis.com/projects/PROJECT_ID/locations/LOCATION/buckets/BUCKET_ID`,
  `storage.googleapis.com/BUCKET_NAME`, `bigquery.googleapis.com/projects/.../datasets/...`,
  or `pubsub.googleapis.com/projects/.../topics/...`.
- `filter` — a Logging query-language expression. An empty filter routes everything.
- `includeChildren` — only meaningful on a folder or organization sink.
- `disabled` — create it disabled if you want to stage the change.

The response carries `writerIdentity`, a service account Google mints for this sink.

## 3. Grant the writer identity — the step that is always missed

The sink does nothing until `writerIdentity` has write access on the destination: Storage
Object Creator on a GCS bucket, BigQuery Data Editor on a dataset, Pub/Sub Publisher on a
topic, Logs Bucket Writer on a log bucket. Until then routing fails silently — no error is
returned on the create call.

## 4. Verify

Write a matching entry (see the write-and-query skill), then read at the destination. If
nothing arrives, check the writer identity grant before touching the filter.

## Reversibility — read this before deleting

Deleting a sink is **not reversible**, and entries that were not routed while the sink was
missing are **not backfilled**. That loss is permanent. If you need to stop routing
temporarily, set `disabled: true` instead of deleting.

Contrast with log buckets, which are reversible: a deleted bucket sits in `DELETE_REQUESTED`
for 7 days and can be restored with `buckets.undelete` (and Logging keeps routing to it during
that window).

## Errors

Same `google.rpc.Status` envelope as the rest of the API — branch on `error.status`.
`FAILED_PRECONDITION` or `INVALID_ARGUMENT` on create usually means a malformed destination
resource name; `PERMISSION_DENIED` means the caller, not the writer identity, lacks the grant.
