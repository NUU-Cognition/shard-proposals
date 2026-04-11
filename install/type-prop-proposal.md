---
id: b7e2a4c1-3d8f-4e6a-9b0c-5f7d1e2a3b4c
tags:
  - "#f/metadata"
  - "#f/type"
---

# Proposal

A structured decision document that captures research, options, trade-offs, and a recommendation for a change or feature. Proposals have a formal review lifecycle that gates them before they become actionable tasks.

## Properties

| Property | Value |
|----------|-------|
| Tag | `#prop/proposal` |
| Location | `Mesh/Types/Proposals/` |
| Archive | `Mesh/Archive/Proposals/` |
| Naming | `(Proposal) NNN [Name].md` |
| Numbering | `flint helper type newnumber Proposal` |

## Lifecycle

```
draft → open → reviewing → approved | rejected | deferred

Any status → deprecated (terminal)
```

## Templates

- [[tmp-prop-proposal-v0.1]] — Standard proposal
