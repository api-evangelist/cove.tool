---
name: cove.tool-provision-team-access
description: >-
  Provision and inspect cove.tool user accounts on an organization's license — create a user via
  the signup endpoint, then read the resulting profile to confirm business membership and admin
  standing. Use when onboarding teammates onto a cove.tool license programmatically.
generated: '2026-08-11'
method: generated
source: openapi/cove.tool-rest-api-v2-openapi.yml
api: cove.tool REST API v2
base_url: https://app.covetool.com/api/v2
operations:
  - POST /auth/signup
  - GET /profiles/{profile_id}
operation_id_note: >-
  cove.tool's published OpenAPI declares no operationId. This skill binds to method + path. The
  names createUserAccount and getProfile come from
  overlays/cove.tool-rest-api-v2-overlay.yaml and are API Evangelist assignments.
---

# Provision cove.tool team access

## What this flow does

cove.tool licenses are held by a **business**, and users are **profiles** inside it. This flow adds
a profile to your business's license and then verifies it landed correctly.

## Step 1 — create the account

```
POST /auth/signup
```

```json
{
  "email": "person@example.com",
  "password": "<a generated secret>",
  "first_name": "Jane",
  "last_name": "Smith"
}
```

All four fields are required. Expect **201**.

**Read the security posture of this endpoint before you wire it into anything.** `POST /auth/signup`
is the only operation in the entire v2 specification that declares **no security requirement** — it
is unauthenticated, and it adds a user account that can access cove.tool products and features
under your organization's license. Treat it as a privileged, abusable surface:

- Never expose it through an agent tool, a public form, or anything a user can drive directly.
- Generate the password yourself; never echo it back into a log, a transcript, or a tool result.
- Rate-limit it on your own side. cove.tool publishes no rate limits, returns no `RateLimit-*` or
  `Retry-After` headers, and declares no 429 — there is no server-side signal telling you that you
  are creating accounts too fast.
- There is no idempotency mechanism, so a retried signup is a second creation attempt, not a
  no-op. On a timeout, verify with step 2 before retrying.

## Step 2 — verify the profile

```
GET /profiles/{profile_id}
```

Returns `data` with `is_owner`, `is_admin`, `created_at`, `email`, `first_name`, `last_name` and
`business`. Confirm:

- `business` matches your organization — a profile outside your business returns **403**, and that
  403 is the meaningful check, not an error to swallow.
- `is_owner` / `is_admin` are what you intended. Nothing in this API sets them; role assignment is
  not exposed as an operation, so if they are wrong you must fix it in the web application at
  https://app.covetool.com/.

A **404** means the profile id does not exist or is not visible to your token.

## What this API cannot do

There is no list-profiles operation, no update-profile, no deactivate or delete, and no
role-assignment endpoint. You can create a user and read one user by id, and that is the whole
identity surface. Deprovisioning a departing employee is a web-application task — plan for it,
because an automated onboarding flow with no automated offboarding flow is how orphaned licensed
accounts accumulate.

## Failure handling

| Status | Meaning | What to do |
|---|---|---|
| 400 | Bad Request | A required signup field is missing or malformed |
| 403 | No permission | The profile is outside your business — this is the boundary working |
| 404 | Not found | No such profile id, or not visible to this token |

The 401 body on this API is `{"detail": "..."}` even though the spec declares
`{data, msg, errors}` — handle both. Capture `x-cove-unique-trace-id` from any failed response
before you retry.
