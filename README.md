# Google Cloud Logging

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Google Cloud Logging is a fully managed, real-time log management service that ingests, stores, searches, analyzes, routes and alerts on application and system log data at scale across Google Cloud, AWS and on-premises environments. The v2 API writes log entries and manages the configuration surface behind them — log buckets and views, Log Router sinks and exclusions, logs-based metrics, log scopes, linked BigQuery datasets and CMEK settings. Google publishes it as a Discovery document with 254 methods, as first-party gRPC service definitions, through seven official client libraries and the gcloud logging command group, and — since April 2026 — through a fully managed remote MCP server at logging.googleapis.com/mcp that exposes six read-only tools to agents.

**Areas:** Cloud · Logging · Monitoring · Observability · Telemetry · Log Management · SRE · DevOps · OpenTelemetry · Google Cloud

## Google Cloud Logging on APIs.io

Everything profiled for Google Cloud Logging is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/google-cloud-logging/](https://apis.io/providers/google-cloud-logging/)** — or go straight to one of the APIs or properties below.

### APIs (9)

- [Google Cloud Logging Bucket API](https://apis.io/apis/google-cloud-logging/google-cloud-logging-bucket-api/) — The Bucket API from Google Cloud Logging — 1 operation(s) for bucket.
- [Google Cloud Logging Buckets API](https://apis.io/apis/google-cloud-logging/google-cloud-logging-buckets-api/) — The Buckets API from Google Cloud Logging — 1 operation(s) for buckets.
- [Google Cloud Logging Entries:copy API](https://apis.io/apis/google-cloud-logging/google-cloud-logging-entries-copy-api/) — The Entries:copy API from Google Cloud Logging — 1 operation(s) for entries:copy.
- [Google Cloud Logging Entries:list API](https://apis.io/apis/google-cloud-logging/google-cloud-logging-entries-list-api/) — The Entries:list API from Google Cloud Logging — 1 operation(s) for entries:list.
- [Google Cloud Logging Entries:tail API](https://apis.io/apis/google-cloud-logging/google-cloud-logging-entries-tail-api/) — The Entries:tail API from Google Cloud Logging — 1 operation(s) for entries:tail.
- [Google Cloud Logging Entries:write API](https://apis.io/apis/google-cloud-logging/google-cloud-logging-entries-write-api/) — The Entries:write API from Google Cloud Logging — 1 operation(s) for entries:write.
- [Google Cloud Logging Exclusions API](https://apis.io/apis/google-cloud-logging/google-cloud-logging-exclusions-api/) — The Exclusions API from Google Cloud Logging — 1 operation(s) for exclusions.
- [Google Cloud Logging Google Cloud Logging API](https://apis.io/apis/google-cloud-logging/google-cloud-logging-google-cloud-logging-api-api/) — The Google Cloud Logging API API from Google Cloud Logging — 1 operation(s) for google cloud logging api.
- [Google Cloud Logging Sinks API](https://apis.io/apis/google-cloud-logging/google-cloud-logging-sinks-api/) — The Sinks API from Google Cloud Logging — 1 operation(s) for sinks.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [Cloud Logging MCP server](https://apis.io/servers/google-cloud-logging/cloud-logging-mcp-server/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Google Cloud Logging Agentic Access](https://apis.io/agentic-access/google-cloud-logging/google-cloud-logging-agentic-access/)

#### Collections (10)

Postman and Open Collection request collections.

- [Google Cloud Logging API](https://apis.io/collections/google-cloud-logging/open-google-cloud-logging/)
- [Google Cloud Logging Bucket API](https://apis.io/collections/google-cloud-logging/open-google-cloud-logging-bucket-api/)
- [Google Cloud Logging Bucket Buckets API](https://apis.io/collections/google-cloud-logging/open-google-cloud-logging-buckets-api/)
- [Google Cloud Logging Bucket Entries:copy API](https://apis.io/collections/google-cloud-logging/open-google-cloud-logging-entries-copy-api/)
- [Google Cloud Logging Bucket Entries:list API](https://apis.io/collections/google-cloud-logging/open-google-cloud-logging-entries-list-api/)
- [Google Cloud Logging Bucket Entries:tail API](https://apis.io/collections/google-cloud-logging/open-google-cloud-logging-entries-tail-api/)
- [Google Cloud Logging Bucket Entries:write API](https://apis.io/collections/google-cloud-logging/open-google-cloud-logging-entries-write-api/)
- [Google Cloud Logging Bucket Exclusions API](https://apis.io/collections/google-cloud-logging/open-google-cloud-logging-exclusions-api/)
- [Google Cloud Logging Bucket Google Cloud Logging API API](https://apis.io/collections/google-cloud-logging/open-google-cloud-logging-google-cloud-logging-api-api/)
- [Google Cloud Logging Bucket Sinks API](https://apis.io/collections/google-cloud-logging/open-google-cloud-logging-sinks-api/)

#### Overlays (18)

OpenAPI overlays, including conversational phrasing for each operation.

- [Google Cloud Logging Api Api Overlay](https://apis.io/overlays/google-cloud-logging/google-cloud-logging-api-api-overlay/)
- [Google Cloud Logging Bucket Api Overlay](https://apis.io/overlays/google-cloud-logging/google-cloud-logging-bucket-api-overlay/)
- [Google Cloud Logging Bucket Api Phrasing Overlay](https://apis.io/overlays/google-cloud-logging/google-cloud-logging-bucket-api-phrasing-overlay/)
- [Google Cloud Logging Buckets Api Overlay](https://apis.io/overlays/google-cloud-logging/google-cloud-logging-buckets-api-overlay/)
- [Google Cloud Logging Buckets Api Phrasing Overlay](https://apis.io/overlays/google-cloud-logging/google-cloud-logging-buckets-api-phrasing-overlay/)
- [Google Cloud Logging Entries Copy Api Overlay](https://apis.io/overlays/google-cloud-logging/google-cloud-logging-entries-copy-api-overlay/)
- [Google Cloud Logging Entries Copy Api Phrasing Overlay](https://apis.io/overlays/google-cloud-logging/google-cloud-logging-entries-copy-api-phrasing-overlay/)
- [Google Cloud Logging Entries List Api Overlay](https://apis.io/overlays/google-cloud-logging/google-cloud-logging-entries-list-api-overlay/)
- [Google Cloud Logging Entries List Api Phrasing Overlay](https://apis.io/overlays/google-cloud-logging/google-cloud-logging-entries-list-api-phrasing-overlay/)
- [Google Cloud Logging Entries Tail Api Overlay](https://apis.io/overlays/google-cloud-logging/google-cloud-logging-entries-tail-api-overlay/)
- [Google Cloud Logging Entries Tail Api Phrasing Overlay](https://apis.io/overlays/google-cloud-logging/google-cloud-logging-entries-tail-api-phrasing-overlay/)
- [Google Cloud Logging Entries Write Api Overlay](https://apis.io/overlays/google-cloud-logging/google-cloud-logging-entries-write-api-overlay/)
- [Google Cloud Logging Entries Write Api Phrasing Overlay](https://apis.io/overlays/google-cloud-logging/google-cloud-logging-entries-write-api-phrasing-overlay/)
- [Google Cloud Logging Exclusions Api Overlay](https://apis.io/overlays/google-cloud-logging/google-cloud-logging-exclusions-api-overlay/)
- [Google Cloud Logging Exclusions Api Phrasing Overlay](https://apis.io/overlays/google-cloud-logging/google-cloud-logging-exclusions-api-phrasing-overlay/)
- [Google Cloud Logging Google Cloud Logging Api Api Phrasing Overlay](https://apis.io/overlays/google-cloud-logging/google-cloud-logging-google-cloud-logging-api-api-phrasing-overlay/)
- [Google Cloud Logging Sinks Api Overlay](https://apis.io/overlays/google-cloud-logging/google-cloud-logging-sinks-api-overlay/)
- [Google Cloud Logging Sinks Api Phrasing Overlay](https://apis.io/overlays/google-cloud-logging/google-cloud-logging-sinks-api-phrasing-overlay/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Google Cloud Logging Authentication](https://apis.io/security/google-cloud-logging/google-cloud-logging-authentication/)
- [Google Cloud Logging Domain Security](https://apis.io/security/google-cloud-logging/google-cloud-logging-domain-security/)
- [Google Cloud Logging Trust Center](https://apis.io/security/google-cloud-logging/google-cloud-logging-trust-center/)
- [Google Cloud Logging Vulnerability Disclosure](https://apis.io/security/google-cloud-logging/google-cloud-logging-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Google Cloud Logging Scopes](https://apis.io/scopes/google-cloud-logging/google-cloud-logging-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Google Cloud Logging Plans Pricing](https://apis.io/plans/google-cloud-logging/google-cloud-logging-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Google Cloud Logging Rate Limits](https://apis.io/rate-limits/google-cloud-logging/google-cloud-logging-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Google Cloud Logging Finops](https://apis.io/finops/google-cloud-logging/google-cloud-logging-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://cloud.google.com)
- [Documentation](https://cloud.google.com/logging/docs)
- [Getting started](https://cloud.google.com/logging/docs/quickstart)
- [Pricing](https://cloud.google.com/stackdriver/pricing)
- [Support](https://cloud.google.com/support)
- [Changelog](https://cloud.google.com/logging/docs/release-notes)
- [Blog](https://cloud.google.com/blog/products/operations)
- [Security](https://g.co/vrp)
- [Compliance](https://cloud.google.com/security/compliance)
- [Terms of service](https://cloud.google.com/terms)
- [Privacy policy](https://policies.google.com/privacy)
- [GitHub](https://github.com/googleapis)
- [Status](https://status.cloud.google.com/)

## API Evangelist rating

**Kin Score 66.1** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 71.7 |
| Contract quality | 46.2 |
| Contract governance | 18.2 |
| Operational transparency | 84.2 |
| Developer ergonomics | 83.9 |
| Access clarity | 68.4 |

**Agent readiness 47.9** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | documented (partial credit) |
| Auth Clarity | served (partial credit) |
| Idempotency | documented (partial credit) |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | yes |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | yes |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 45.1** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/google-cloud-logging/](https://apis.io/providers/google-cloud-logging/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Google Cloud Logging: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/google-cloud-logging/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
