# Reeple API — Postman Collection

Transcribed from [`api-reference/`](../api-reference) (42 documented `.mdx` files, 45 requests — a couple of files bundle multiple operations: CAD collection emails covers add/list/delete, and source-of-funds covers URL submission plus a file-upload variant). There's no OpenAPI spec backing these docs, so this collection is hand-built to mirror them.

## Import

1. In Postman: **Import** → select both `reeple-api.postman_collection.json` and `reeple-api.postman_environment.json`.
2. Pick **Reeple API** from the environment dropdown (top right).
3. Open the environment, paste your secret key into `apiKey` (`sk_test_...` for sandbox, `sk_live_...` for production).
4. Send any request. `baseUrl` and auth are already wired up — no per-request setup needed.

## Notes

- Auth (`api-key` header) is set once at the collection level and inherited by every request.
- There's no separate sandbox hostname — the environment is determined by which key prefix you use.
- Requests with path variables (`:id`, `:reference`, etc.) ship with realistic example defaults pulled from the docs, so they run as-is; swap in your own values as needed.
- Endpoints with multiple currency-specific request bodies (e.g. **Payouts > Initiate payout**) ship with one live example body; the other currency variants are included as reference JSON in the request's description tab.
- A light collection-level test (Tests tab) checks for a 2xx response on every request — informational only, since some flows (AML, insufficient balance, etc.) legitimately expect non-2xx responses.
