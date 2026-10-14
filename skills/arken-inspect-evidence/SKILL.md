---
name: arken-inspect-evidence
description: Use an ARKEN deal category to identify negotiable terms and evidence gaps before a negotiation. Apply when the user wants a preparation checklist grounded in the public ARKEN catalog.
metadata:
  author: ARKEN
  version: "1.0.0"
---

Inspect the evidence requirements for the user's negotiation category. Obtain a real `domain_id` from ARKEN catalog search first; do not guess one.

With an ARKEN MCP connection, call `arken_get_deal_type` using that `domain_id`. Without MCP, fetch the public catalog and select the exact matching record locally:

```sh
curl --fail-with-body 'https://usearken.com/api/v1/deal-types'
```

Read `what_is_valued`, `negotiable_terms`, `required_evidence`, and `relationship_examples`. Turn them into a useful preparation checklist, separating:

- Facts supported by information the user supplied.
- Evidence still needed to assess those facts.
- Terms the parties could negotiate.

For example, a supplier-renewal conversation may require the current contract, actual usage, service commitments, comparable offers, renewal deadlines, and switching costs. Use the returned category to decide which items apply; don't imply the example is exhaustive.

Keep illustrative scales separate from actual deal values. A catalog record does not verify documents, determine enforceability, or establish fair market value. Ask only for missing information that changes the next step. This workflow does not upload documents or access private workspace cases.

No authentication or payment is required. Respect `Retry-After` on 429 and distinguish service errors from a missing category.

Public reference: https://usearken.com/docs/api
Official publisher: https://usearken.com
