# ARKEN agent skills

Official skills for [ARKEN](https://usearken.com), negotiation and conflict-resolution software. Use the public catalog to find a deal category, inspect the evidence needed, and prepare an unsaved draft for human review.

## Install

```sh
npx skills add lantos1618/arken-agent-skills
```

The three skills are available together in this repository:

| Skill | Use it to |
| --- | --- |
| `arken-search-deal-types` | Match a situation to public negotiation categories |
| `arken-inspect-evidence` | Identify relevant interests, terms, and evidence gaps |
| `arken-prepare-case-draft` | Prepare an editable, unsaved draft from supplied notes |

No ARKEN account or API key is needed for these public operations. The skills use an available ARKEN MCP connection or the public REST API. They do not save private workspace cases, run model analysis, or send messages.

## Other interfaces

- [Developer guide](https://usearken.com/developers)
- [API reference](https://usearken.com/docs/api)
- [OpenAPI contract](https://usearken.com/openapi.json)
- [MCP server](https://usearken.com/mcp)
- [CLI and SDK downloads](https://usearken.com/docs/sdk)
- [A2A integration](https://usearken.com/docs/a2a)
- [Privacy](https://usearken.com/privacy)

## ChatGPT / Codex plugin package

`plugin.json`, `mcp.json`, the skills, and the icon assets form a portable plugin package for the public ARKEN MCP server. This repository is the source package; publication here does not mean the plugin has been accepted into the ChatGPT directory.

Report issues in this repository, or use [ARKEN contact information](https://usearken.com/contact).

The included screenshot was captured in a local MCP test host with synthetic notes. It is not evidence of ChatGPT directory approval.
