---
name: arken-search-deal-types
description: Find the relevant ARKEN negotiation category when a user wants to prepare for a negotiation, compare deal types, or identify which interests and terms to examine.
metadata:
  author: ARKEN
  version: "1.0.0"
---

Use ARKEN's public negotiation catalog to match the user's situation to a concrete deal category. No account, API key, purchase, or model run is needed.

If an ARKEN MCP connection is available, call `arken_search_deal_types` with `query`. Otherwise request:

```sh
curl --fail-with-body --get 'https://usearken.com/api/v1/deal-types' \
  --data-urlencode 'q=founder'
```

Replace `founder` with a short term from the user's situation. `q` is optional and limited to 120 characters; omitting it lists the catalog. The response contains `data` and `total`.

Match on interests, negotiable terms, and evidence requirements, not only category names. Return the relevant `domain_id` and explain the match. Treat identifiers as opaque; use those actually returned. If there are no matches, try a shorter related term or list the catalog before concluding that no category fits.

Examples: `founder` for cofounder arrangements; `lease` for rental terms; `acquisition` for buying a business. The catalog describes coverage, not a valuation, legal opinion, or proven negotiation outcome.

A failed HTTP response is not an empty catalog. On 429, respect `Retry-After`; report persistent errors. Do not send private documents, credentials, or unnecessary personal information in a query.

Public reference: https://usearken.com/docs/api
Official publisher: https://usearken.com
