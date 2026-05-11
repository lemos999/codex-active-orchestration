---
name: graph-locator-boundary
description: Use when graph indexes, dependency graphs, call graphs, Graphify-style systems, or semantic locators are used to narrow context.
---

# Graph Locator Boundary

Graph tools are candidate locators. They help decide where to inspect; they do not replace source reading, tests, citations, or human review. Treat graph edges and summaries as hypotheses until confirmed in original files or authoritative sources.

For each graph-assisted step, record:

```text
locator_tool:
index_version_or_date:
query:
candidates_returned:
files_or_sources_confirmed:
false_positives_or_gaps:
decision:
```

Use graph output to reduce the search set, then open the smallest original source slice needed to verify the claim.

Load repo-root `references/graph-locator-policy.md` for boundaries, provenance, and release notes.
