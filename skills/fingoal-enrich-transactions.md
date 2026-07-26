---
name: Enrich a batch of transactions with FinGoal
description: Submit raw transactions to the FinGoal Insights API, then retrieve enriched results (clean merchant names, categories, and Persona Tags) by polling or webhook.
api: openapi/fingoal-insights-openapi-original.json
operations:
- asyncCleanupTransactions
- getEnrichment
- upsertWebhookConfiguration
---

# Enrich a batch of transactions

Use this to turn raw bank/card transactions into cleaned, categorized, tagged
records via the FinGoal Insights API (base URL `https://findmoney.fingoal.com/v3`,
dev `https://findmoney-dev.fingoal.com/v3`).

## 1. Get a token
POST `/authentication` with a JSON body `{"client_id": "...", "client_secret": "..."}`.
Read `access_token` from the response and send it as `Authorization: Bearer <access_token>`
on every subsequent call. Requires the `enrichment` scope.

## 2. (Optional) register a webhook
`upsertWebhookConfiguration` (PUT `/webhook-configurations`) with `webhook_type:
ENRICHMENT_DATA` and an HTTPS `callback_url` so results are pushed when the batch
finishes. Include the `client_id` header.

## 3. Submit the batch
`asyncCleanupTransactions` (POST `/cleanup`) with `{ "transactions": [ ... ] }`.
The response returns `batch_request_id`, `transactions_received`,
`transactions_validated`, `processing`, and `num_transactions_processing`.

## 4. Get results
Either wait for the `ENRICHMENT_DATA` webhook (carries `enrichedTransactions[]`
and `failedTransactions[]`), or poll `getEnrichment` (GET
`/cleanup/{batch_request_id}`) using the id from step 3.

## Rules
- Errors are not RFC 9457: a `400` returns an array of per-field validation
  errors; a `401` means re-mint the token; a `404` on `getEnrichment` means the
  `batch_request_id` is unknown. See `errors/fingoal-problem-types.yml`.
- No idempotency key is supported; do not blind-retry a submit — a retry creates
  a new batch. See `conventions/fingoal-conventions.yml`.
- For quick testing use `syncCleanupTransactions` (POST `/cleanup/sync`), which
  returns enriched results inline instead of async.
