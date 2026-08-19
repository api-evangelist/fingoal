---
name: Link a bank account with FinGoal Link Money
description: Mint a tenant-scoped Link Money JWT, fetch Yodlee FastLink 4 session details, and open the account-linking widget for a user.
api: openapi/_original/fingoal-link-money-openapi-original.json
operations:
- oauthToken
- getFastlinkFourDetails
- getClient
---

# Link an account with Link Money

Link Money is an authentication portal in front of a shared Yodlee aggregation
instance. You authenticate as a developer against one **tenant** (a bank or
credit union), then hand the user off to Yodlee's FastLink 4 widget.

## 0. Get credentials first

There is no self-serve signup. Request access at
<https://fingoal.com/request-developer-account>; FinGoal reviews the request and
emails a secure link to your `clientId` / `clientSecret`. Every Link Money
developer gets a development-environment `tenantId`. To reach a real bank's
tenant, email support@fingoal.com — you cannot create tenants yourself.

## 1. Mint a tenant-scoped token

`oauthToken` — POST `/api/oauth/token` with `{ clientId, clientSecret, tenantId }`.
The response carries `token`.

- The JWT is valid for **1 hour**.
- It grants access to **one tenant only**. Working across tenants means minting
  one token per tenant — cache them per `tenantId`, not per client.
- Send it as `Authorization: Bearer <token>` on every later call.

## 2. (Optional) Confirm what this credential can reach

`getClient` — GET `/client` returns your client configuration, including the
tenants you are authorized for. Useful as a pre-flight when a call starts
returning 401/403 and you are unsure whether the token or the tenant is wrong.

## 3. Fetch FastLink session details

`getFastlinkFourDetails` — POST `/yodlee/fastlink/get` with `{ loginName }` for
the end user. The response has two fields:

- `accessToken` — a user-specific Yodlee access token.
- `fastLinkURL` — a tenant-specific widget URL.

Neither is a FinGoal-durable identifier; treat both as short-lived session
material and never persist them.

## 4. Open the widget in the frontend

Load Yodlee's loader (`https://cdn.yodlee.com/fastlink/v4/initialize.js`) and
call `window.fastlink.open({ fastLinkURL, accessToken: 'Bearer ' + accessToken,
params: { configName }, onSuccess, onError, onClose, onEvent },
'container-fastlink')`.

`configName` selects the flow, and only these four are provisioned per tenant by
default:

| configName | behavior |
|---|---|
| `aggregation` | mandatory account aggregation |
| `verification` | mandatory account verification |
| `aggregation_and_verification` | mandatory aggregation, optional verification |
| `verification_and_aggregation` | mandatory verification, optional aggregation |

See `components/fingoal-components.yml`. FinGoal warns that some FastLink
functionality (e.g. FastLink Configuration) may not be exposed through Link
Money.

## 5. Read the linked data

Past the operations described above, Link Money is a **direct proxy** to the
Yodlee Core API and surfaces those endpoints unaltered — e.g. GET
`/api/yodlee/accounts`. One deviation matters: put the user's `loginName` in a
request **header**, not in the payload. Those proxied endpoints are not in
FinGoal's OpenAPI, so consult the Yodlee Core API reference for their shapes.

## 6. Get told when data changes

Register a webhook rather than polling — see
`skills/fingoal-link-money-webhooks.md` and
`asyncapi/fingoal-link-money-webhooks.yml`.

## Rules

- Base URL: `https://link-money-dev.fingoal.dev/api`. This is the only host
  FinGoal publishes; the OpenAPI `servers[]` entry omits the `/api` prefix that
  every documented example uses, so build request URLs from the examples.
- No idempotency key, no pagination, and no rate-limit response header exists on
  this API. See `conventions/fingoal-conventions.yml`.
- Aggregation coverage is not instant: FinGoal's developer FAQ says open-banking
  institutions typically appear within ~2 weeks of initiation and most
  connections are ready in 6–8 weeks. Historical lookback varies by institution —
  up to 365 days over open banking, 90–720 days via screen scraping.
