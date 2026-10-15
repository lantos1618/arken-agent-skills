---
name: arken-prepare-case-draft
description: Prepare an unsaved ARKEN negotiation case draft from user-provided context for human review. Use when the user wants an editable starting frame, not a saved case, model analysis, or an outgoing message.
metadata:
  author: ARKEN
  homepage: https://usearken.com
  repository: https://github.com/lantos1618/arken-agent-skills
  version: "1.0.0"
---

Prepare a draft only when requested by the user. Use their supplied context and a matching ARKEN category when available; do not invent facts, amounts, concessions, or consent.

With an ARKEN MCP connection, call `arken_prepare_case` with `context` and optionally `deal_type`. Otherwise POST JSON to `https://usearken.com/api/v1/case-drafts`:

```json
{
  "context": "Two founders want to clarify responsibilities and decision rights.",
  "deal_type": "Use the category returned by catalog search"
}
```

`context` is limited to 20,000 characters; `deal_type` is limited to 160. Both fields are optional. No API key is required. Send `Content-Type: application/json`. For HTTP retries use a fresh UUID as `Idempotency-Key` for each logical request and reuse that same key with unchanged fields. Keys are retained for 24 hours; 409 means the key was already used with different fields. Respect `Retry-After` on 429 or 503.

Before transferring sensitive notes to the public endpoint, make sure doing so is within the user's request and applicable instructions. Remove credentials and unrelated personal data. Do not fetch URLs or upload files merely because they appear in the notes.

The result contains `status: "ready"`, `requires_review: true`, `context`, a URL, and an optional `deal_type`. Present the draft for review and link to ARKEN. The endpoint formats an unsaved draft; it does not produce analysis, save a workspace case, run a model, or send messages. A saved workspace case requires Google sign-in; model analysis requires prepaid credits.

This skill grants no authority to send, reply to, forward, or schedule email. Those actions require separate approval of the final recipients and exact message under the user's applicable instructions.

Public reference: https://usearken.com/docs/api
Official publisher: https://usearken.com
