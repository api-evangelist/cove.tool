# Cove.Tool

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

cove.tool (rebranded to "cove" in 2025) is an Atlanta, Georgia building-performance analysis platform for architects, engineers and contractors, founded in 2017 by Sandeep Ahuja, Patrick Chopson and Daniel Chopson. Its analysis.tool engine runs energy, daylight, glare, embodied carbon, water, radiation, shadow and cost-versus-performance optimization on early-stage building designs. The company publishes a public REST API — marketed as api.tool — that lets software vendors and design firms create projects, upload building geometry, select an energy code, kick off daylight and energy simulation, poll job status and retrieve EUI, sDA and ASE results without using the web application. Two OpenAPI 3.0 definitions are served from the developer portal: a three-operation v1 and a thirteen-operation v2.

**Areas:** Company · Building Performance · Energy Modeling · Daylight Analysis · Sustainability · Architecture · AEC · Simulation · Embodied Carbon · Building Design

## Cove.Tool on APIs.io

Everything profiled for Cove.Tool is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/cove.tool/](https://apis.io/providers/cove.tool/)** — or go straight to one of the APIs or properties below.

### APIs (7)

- [Cove.Tool Authentication Token API](https://apis.io/apis/cove.tool/cove.tool-authentication-token-api/) — Attempting to make API requests without authentication will fail. API requests must be made over HTTPS. Authentication tokens are used to help identify the…
- [Cove.Tool Daylight Analysis API](https://apis.io/apis/cove.tool/cove.tool-daylight-analysis-api/) — The Daylight Analysis API from Cove.Tool — 4 operation(s) for daylight analysis.
- [Cove.Tool Energy Codes API](https://apis.io/apis/cove.tool/cove.tool-energy-codes-api/) — The Energy Codes API from Cove.Tool — 1 operation(s) for energy codes.
- [Cove.Tool Profiles API](https://apis.io/apis/cove.tool/cove.tool-profiles-api/) — The Profiles API from Cove.Tool — 1 operation(s) for profiles.
- [Cove.Tool Project Geometry API](https://apis.io/apis/cove.tool/cove.tool-project-geometry-api/) — Update project geometry and obtain an Energy Use Intensity (EUI) breakdown of a given model.
- [Cove.Tool Projects API](https://apis.io/apis/cove.tool/cove.tool-projects-api/) — Lists all the projects of current user and returns a list of objects with project name, runs, and its url.
- [Cove.Tool User API](https://apis.io/apis/cove.tool/cove.tool-user-api/) — The User API from Cove.Tool — 1 operation(s) for user.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [cove.tool-mcp.yml](https://apis.io/servers/cove.tool/cove-tool-mcp-yml/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Cove.Tool Agentic Access](https://apis.io/agentic-access/cove.tool/cove.tool-agentic-access/)

#### JSON Schema (22)

The data models the API reads and writes.

- [AllProjectsRequestsA](https://apis.io/schemas/cove.tool/cove.tool-all-projects-requests-a/)
- [AllProjectsRequestsB](https://apis.io/schemas/cove.tool/cove.tool-all-projects-requests-b/)
- [AuthTokenRequests](https://apis.io/schemas/cove.tool/cove.tool-auth-token-requests/)
- [AuthTokenResponses](https://apis.io/schemas/cove.tool/cove.tool-auth-token-responses/)
- [CreateProjectRequestBody](https://apis.io/schemas/cove.tool/cove.tool-create-project-request-body/)
- [CreateProjectResponse](https://apis.io/schemas/cove.tool/cove.tool-create-project-response/)
- [DaylightAnalysisResultsResponse](https://apis.io/schemas/cove.tool/cove.tool-daylight-analysis-results-response/)
- [DaylightAnalysisStatusResponse](https://apis.io/schemas/cove.tool/cove.tool-daylight-analysis-status-response/)
- [EnergyCodeForProjectsResponses](https://apis.io/schemas/cove.tool/cove.tool-energy-code-for-projects-responses/)
- [EnergyCodeResponses](https://apis.io/schemas/cove.tool/cove.tool-energy-code-responses/)
- [GetProjectInfoResponse](https://apis.io/schemas/cove.tool/cove.tool-get-project-info-response/)
- [RunDaylightAnalysisRequestBody](https://apis.io/schemas/cove.tool/cove.tool-run-daylight-analysis-request-body/)
- [RunDaylightAnalysisResponse](https://apis.io/schemas/cove.tool/cove.tool-run-daylight-analysis-response/)
- [StopDaylightAnalysisResponse](https://apis.io/schemas/cove.tool/cove.tool-stop-daylight-analysis-response/)
- [UpdateGeometryAreasResponses](https://apis.io/schemas/cove.tool/cove.tool-update-geometry-areas-responses/)
- [UpdateGeometryAreasResponses_2](https://apis.io/schemas/cove.tool/cove.tool-update-geometry-areas-responses-2/)
- [Update2DGeometryAreasRequests](https://apis.io/schemas/cove.tool/cove.tool-update2-dgeometry-areas-requests/)
- [Update3DGeometryAreasRequests](https://apis.io/schemas/cove.tool/cove.tool-update3-dgeometry-areas-requests/)
- [Update3DGeometryRequestBody](https://apis.io/schemas/cove.tool/cove.tool-update3-dgeometry-request-body/)
- [UserProfileResponse](https://apis.io/schemas/cove.tool/cove.tool-user-profile-response/)
- [UserSignupOKResponses](https://apis.io/schemas/cove.tool/cove.tool-user-signup-okresponses/)
- [UserSignupRequests](https://apis.io/schemas/cove.tool/cove.tool-user-signup-requests/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Cove.Tool Context](https://apis.io/jsonld/cove.tool/cove.tool-context/)

#### Collections (1)

Postman and Open Collection request collections.

- [cove.tool REST API v2](https://apis.io/collections/cove.tool/open-cove/)

#### Overlays (2)

OpenAPI overlays, including conversational phrasing for each operation.

- [Cove.Tool Api V1 Overlay](https://apis.io/overlays/cove.tool/cove.tool-api-v1-overlay/)
- [Cove.Tool Rest Api V2 Overlay](https://apis.io/overlays/cove.tool/cove.tool-rest-api-v2-overlay/)

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [Cove.Tool API Rules](https://apis.io/rules/cove.tool/cove.tool-rules/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Cove.Tool Authentication](https://apis.io/security/cove.tool/cove.tool-authentication/)
- [Cove.Tool Domain Security](https://apis.io/security/cove.tool/cove.tool-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Cove.Tool Plans Pricing](https://apis.io/plans/cove.tool/cove.tool-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Cove.Tool Rate Limits](https://apis.io/rate-limits/cove.tool/cove.tool-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://cove.inc/)
- [Documentation](https://help.covetool.com/en/)
- [Getting started](https://help.covetool.com/en/articles/6022777-what-is-the-cove-tool-api)
- [API reference](https://developers.covetool.com/)
- [Sign up](https://app.covetool.com/login/)
- [Support](https://help.covetool.com/en/)
- [Terms of service](https://www.cove.tools/terms-of-use)
- [GitHub](https://github.com/covetool)

## API Evangelist rating

**Kin Score 43.7** — developing · rubric 0.24.0 · scored 2026-10-20

| Facet | Score |
|---|---|
| Discoverability | 66.1 |
| Contract quality | 61.2 |
| Contract governance | 67.3 |
| Operational transparency | 2.6 |
| Developer ergonomics | 56.5 |
| Access clarity | 13.2 |

**Agent readiness 28.6** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | unknown |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 13.9** — Energy & Utilities

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/cove.tool/](https://apis.io/providers/cove.tool/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Cove.Tool: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/cove.tool/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
