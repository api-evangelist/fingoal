---
name: Manage FinGoal Insights API webhooks
description: List, create/update, test, and delete FinGoal webhook configurations for ENRICHMENT_DATA and USER_TAGS_DATA events.
api: openapi/fingoal-insights-openapi-original.json
operations:
- listWebhookConfigurations
- upsertWebhookConfiguration
- testWebhook
- deleteWebhookConfiguration
---

# Manage webhooks

## 1. Authenticate
Mint a JWT at POST `/authentication`; send `Authorization: Bearer <token>` and
the `client_id` header. All webhook operations require the `enrichment` scope.

## 2. List existing configurations
`listWebhookConfigurations` (GET `/webhook-configurations`).

## 3. Create or update
`upsertWebhookConfiguration` (PUT `/webhook-configurations`) with `webhook_type`
(`ENRICHMENT_DATA` or `USER_TAGS_DATA`) and a valid HTTPS `callback_url`. The
response echoes `id`, `client_id`, `tenant_id`, `webhook_type`, `callback_url`,
`created_at`, `updated_at`.

## 4. Test delivery
`testWebhook` (POST `/webhook-configurations/test`) sends a sample payload of the
given `webhook_type` to your callback so you can verify handling before go-live.

## 5. Remove
`deleteWebhookConfiguration` (DELETE `/webhook-configurations`) for the given
`webhook_type`.

## Rules
- `400` enumerates the exact bad field (`client_id header is required`,
  `webhook_type is required`, `Invalid webhook_type`, `callback_url is required`,
  `callback_url must be a valid URL`).
- `403` means the token lacks the `enrichment` scope or the client has no
  relationship with the specified tenant. See `errors/fingoal-problem-types.yml`.
