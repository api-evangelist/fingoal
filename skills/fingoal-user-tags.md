---
name: Retrieve and refresh FinGoal user Persona Tags
description: Trigger a user tag update on the FinGoal Insights API and read back the user's Persona Tags, via sync trigger or the USER_TAGS_DATA webhook.
api: openapi/fingoal-insights-openapi-original.json
operations:
- getOneUser
- getOneUserSync
- getUserTagUpdates
---

# Retrieve and refresh user Persona Tags

## 1. Authenticate
Mint a JWT at POST `/authentication` and send `Authorization: Bearer <token>`.
Reads require the `read` scope; the sync trigger requires `enrichment` +
`calls_to_action`.

## 2. Read a user's current tags
`getOneUser` (GET `/users/{userId}`). Pass the `include_tagged_transactions`
header to include the transactions behind each tag.

## 3. Force a recompute
`getOneUserSync` (GET `/users/{userId}/sync`) triggers a fresh tag update /
calls-to-action refresh for that user.

## 4. Collect updated tags
When a refresh completes, either receive the `USER_TAGS_DATA` webhook (carries
`tenant_id` and `userTags`) or call `getUserTagUpdates` (GET
`/users/tags/{guid}`) with the guid to pull the updated tag set.

## Rules
- A `404` means the userId/guid is unknown. A `401` means re-mint the token.
- Tag meanings live in the public Tag Registry: https://fingoal.com/tags-list.
- See `conventions/fingoal-conventions.yml` and `asyncapi/fingoal-webhooks.yml`.
