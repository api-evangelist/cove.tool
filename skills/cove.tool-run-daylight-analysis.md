---
name: cove.tool-run-daylight-analysis
description: >-
  Run a cove.tool daylight and energy analysis end to end — pick an energy code, create a project,
  upload building geometry, start the run, poll until the job queue drains, and read the EUI, sDA
  and ASE results. Use when an agent needs building-performance numbers for a design and has
  cove.tool credentials.
generated: '2026-08-11'
method: generated
source: openapi/cove.tool-rest-api-v2-openapi.yml
api: cove.tool REST API v2
base_url: https://app.covetool.com/api/v2
operations:
  - GET /energy-codes
  - POST /projects/
  - POST /projects/{project_id}/geometry
  - POST /analysis
  - GET /analysis/{project_id}/status
  - GET /analysis/{project_id}
  - GET /analysis/{project_id}/stop
operation_id_note: >-
  cove.tool's published OpenAPI declares NO operationId on any operation, so this skill binds to
  method + path, which are the provider's own. The names in
  overlays/cove.tool-rest-api-v2-overlay.yaml (listEnergyCodes, createProject,
  uploadProjectGeometry, startAnalysis, getAnalysisStatus, getAnalysisResults, stopAnalysis) are
  API Evangelist assignments, not cove.tool's.
---

# Run a cove.tool daylight and energy analysis

## Prerequisites

You need a **valid trial or licensed cove.tool account** — the API has no self-serve tier. Mint a
token with `POST https://app.covetool.com/api/get-token`, then send it on every call:

```
Authorization: Token <api_token>
```

The scheme word is `Token`, not `Bearer`. A live 401 answers `www-authenticate: Token`.

Every response is wrapped as `{"data": ..., "msg": ..., "errors": [...]}`. Read `.data`.

## Step 1 — choose an energy code

```
GET /energy-codes
GET /energy-codes?name=<partial>
```

Returns `data[]` of `{id, name}`. Keep the `id` — you need it as `energy_code_id` in step 2. If you
already have a project and want only the codes compatible with it, pass `?for_project=<project_id>`
and read the `selected` flag.

## Step 2 — create the project

```
POST /projects/
```

All four fields are required:

```json
{
  "name": "Marietta Office Retail Space",
  "location": "34.177114, -86.830390",
  "building_types": ["Office", "Retail"],
  "energy_code_id": 12
}
```

`location` is a `"lat, lon"` string, not an object. `building_types` is an array — a mixed-use
building lists every use type. Expect **201**; keep `data.id` as your `project_id`.

On 400, the cause is almost always a missing required field. Note that the response schema's
`required` list names `cbecs_eui` while the property it defines is `cebcs_eui` — do not assume
`cbecs_eui` will be present in the body.

## Step 3 — upload the geometry

```
POST /projects/{project_id}/geometry
```

Required: `floors`, `walls`, `windows`, `roofs`, `floor_area`, `roof_area`, `ground_floor_area`,
`building_height`, `si_units`.

**The condition that most often produces a 400 is not in the required list.** You must supply at
least one non-zero value across the cardinal-direction area fields:

- `wall_area_n`, `wall_area_ne`, `wall_area_e`, `wall_area_se`, `wall_area_s`, `wall_area_sw`,
  `wall_area_w`, `wall_area_nw`
- `window_area_n` … `window_area_nw`

A building with all sixteen at zero is rejected. Optional surface collections —
`below_grade_walls`, `outdoor_floors`, `interior_walls`, `spandrels`, `skylights`,
`shading_devices`, `rooms` — plus `skylight_area` and `underground_area` refine the model.

Set `si_units` deliberately: it governs how every area and height above is interpreted.

Expect **201**.

## Step 4 — start the analysis

```
POST /analysis
```

```json
{ "project_id": 33, "analysis_types": ["daylight"] }
```

Expect **202 Accepted**. Results are not in this response.

**Do not blindly retry this call.** It enqueues billable simulation jobs and cove.tool supports no
`Idempotency-Key` — a retry after a timeout can enqueue the work twice with no way to detect it.
If a request times out, go to step 5 and read the status before deciding anything.

## Step 5 — poll until the queue drains

```
GET /analysis/{project_id}/status
```

Returns the **remaining number of jobs per analysis type** for the project. Poll until the count
for your analysis type reaches zero.

There are no webhooks and no callbacks on this API — polling is the only completion signal. There
are also no `RateLimit-*` or `Retry-After` headers to pace yourself against and no declared 429, so
choose a conservative interval yourself (start around 10 seconds and back off) rather than tight-
looping. This endpoint is also the only consumption ceiling cove.tool exposes: if the remaining
count is not what you expect, you may be at your allowance rather than mid-run.

## Step 6 — read the results

```
GET /analysis/{project_id}
```

Returns grid-based daylight results as **per-room meshes** — vertices, triangles, centers and
normals — from which sDA and ASE are read. The project resource itself carries the energy numbers
(`eui`, `cebcs_eui`, `climate_zone`); re-read it with `GET /projects/?project_id=<id>` after the run.

## Cancelling

```
GET /analysis/{project_id}/stop
```

Halts all running calculations for the project.

**Treat this URL as dangerous.** It mutates state on a GET, so it is not safe under RFC 9110
semantics: a cache, crawler, link prefetcher or speculative agent that touches it will cancel a
running simulation. Never put it in a link list, a tool description an agent may explore, or
anything that gets prefetched. Call it only on explicit intent.

## Failure handling

| Status | Meaning | What to do |
|---|---|---|
| 400 | Bad Request | Check required fields; on geometry, check the non-zero cardinal-area rule |
| 401 | Unauthorized | Re-mint the token at `POST /api/get-token`; send `Authorization: Token <t>` |
| 403 | No permission | The profile or project is outside your business |
| 404 | Not found | `project_id` does not exist or is not visible to this token |
| 5xx | Server error | Undeclared in the spec — no typed handling exists; retry with backoff |

The spec declares errors as `{data, msg, errors}`, but the live 401 returns Django REST
Framework's `{"detail": "..."}`. **Handle both shapes.**

Capture the `x-cove-unique-trace-id` response header on every failure — shape
`<uuid>-<unix-timestamp>`, returned even on 401. It is undocumented, and it is the only handle
support has on a request you cannot reproduce.
