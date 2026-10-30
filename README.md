# FinGoal

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

FinGoal provides financial data insights for banks, credit unions, and fintechs. Its Insights API enriches raw bank and card transaction data with clean merchant names, categorization, and behavioral "Persona Tags" that power personalized recommendations, targeted offers, and better banking features. The API is batch-oriented: developers submit transactions, receive a batch_request_id, and collect enriched results by polling or via ENRICHMENT_DATA and USER_TAGS_DATA webhooks. FinGoal also offers Link Money for account aggregation and verification across 17,000+ financial institutions. Authentication uses a JWT minted from client_id/client_secret; developer credentials are issued on request. FinGoal is SOC 2 Type II and GDPR compliant.

**Areas:** Financial Services · Fintech · Transaction Enrichment · Data Enrichment · Personal Financial Management · Banking · Categorization · Webhook

## FinGoal on APIs.io

Everything profiled for FinGoal is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/fingoal/](https://apis.io/providers/fingoal/)** — or go straight to one of the APIs or properties below.

### APIs (7)

- [FinGoal Enrichment API](https://apis.io/apis/fingoal/fingoal-enrichment-api/) — The Insights API's transaction enrichment endpoints enable developers to clean and enhance their transaction data. This process includes standardizing…
- [FinGoal User Tagging API](https://apis.io/apis/fingoal/fingoal-user-tagging-api/) — markdown/tagging.md
- [FinGoal Webhook Configurations API](https://apis.io/apis/fingoal/fingoal-webhook-configurations-api/) — Manage webhook callback URLs for your client. Supports default and tenant-specific configurations per webhook type.
- [FinGoal Client Management API](https://apis.io/apis/fingoal/fingoal-client-management-api/) — There are three kinds of people who interact with Link Money: - **Users** are the people who use the Link Money application. They are the people who log in,…
- [FinGoal Fastlink API](https://apis.io/apis/fingoal/fingoal-fastlink-api/) — The Link Money API permits end users to link and get data from their bank accounts. But of course, that requires a front-end interface. That's where the…
- [FinGoal Webhooks API](https://apis.io/apis/fingoal/fingoal-webhooks-api/) — Webhook payload schemas for all webhook types. Configure which webhooks you receive using the Webhook Configurations endpoints. **Available Webhook Types:**…
- [FinGoal OAUTH API](https://apis.io/apis/fingoal/fingoal-oauth-api/) — The Oauth API from FinGoal — 1 operation(s) for oauth.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (2)

Event-driven and webhook contracts.

- [Fingoal Link Money Webhooks](https://apis.io/asyncapis/fingoal/fingoal-link-money-webhooks/)
- [Fingoal Webhooks](https://apis.io/asyncapis/fingoal/fingoal-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [fingoal-insights](https://apis.io/servers/fingoal/fingoal-insights/)

#### Collections (3)

Postman and Open Collection request collections.

- [Insights Enrichment API](https://apis.io/collections/fingoal/open-fingoal-enrichment-api/)
- [Insights Enrichment User Tagging API](https://apis.io/collections/fingoal/open-fingoal-user-tagging-api/)
- [Insights Enrichment Webhook Configurations API](https://apis.io/collections/fingoal/open-fingoal-webhook-configurations-api/)

#### Overlays (2)

OpenAPI overlays, including conversational phrasing for each operation.

- [Fingoal Insights Overlay](https://apis.io/overlays/fingoal/fingoal-insights-overlay/)
- [Fingoal Link Money Overlay](https://apis.io/overlays/fingoal/fingoal-link-money-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Fingoal Authentication](https://apis.io/security/fingoal/fingoal-authentication/)
- [Fingoal Domain Security](https://apis.io/security/fingoal/fingoal-domain-security/)
- [Fingoal Trust Center](https://apis.io/security/fingoal/fingoal-trust-center/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Fingoal Scopes](https://apis.io/scopes/fingoal/fingoal-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Fingoal Plans Pricing](https://apis.io/plans/fingoal/fingoal-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Fingoal Rate Limits](https://apis.io/rate-limits/fingoal/fingoal-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://fingoal.com/)
- [Documentation](https://docs.fingoal.dev/)
- [Getting started](https://docs.fingoal.dev/)
- [API reference](https://docs.fingoal.dev/)
- [Sign up](https://fingoal.com/request-developer-account)
- [Support](https://fingoal.com/contact)
- [Blog](https://fingoal.com/blog)
- [Compliance](https://fingoal.com/fingoal-privacy-security)
- [Terms of service](https://fingoal.com/terms)
- [Privacy policy](https://fingoal.com/privacy)
- [GitHub](https://github.com/fingoal)

## API Evangelist rating

**Kin Score 54.2** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 58.8 |
| Contract governance | 18.2 |
| Operational transparency | 42.1 |
| Developer ergonomics | 42.3 |
| Access clarity | 50.0 |

**Agent readiness 35.7** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | negotiable (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 43.3** — Banking & Open Finance

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/fingoal/](https://apis.io/providers/fingoal/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for FinGoal: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/fingoal/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
