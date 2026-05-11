# Graph Locator Policy

Graph locators, dependency maps, call graphs, semantic indexes, and Graphify-style tools can reduce search space. They are context routers, not authorities. Their output should point the agent toward original files, tests, commits, documents, or sources.

## Required Provenance

Record tool name, package name when relevant, version or index date, query, returned candidates, and confirmation source. If package naming differs across repository, package manager, and import name, record each explicitly to prevent citation drift.

## Confirmation

Open the original file or source slice before making a claim. For code, confirm symbol definitions, callers, tests, and configuration. For research, confirm against primary documentation or releases. For generated graph summaries, treat natural language descriptions as hypotheses.

## Failure Modes

- Stale index after code changes.
- Missing dynamic calls or generated code.
- Package-name confusion.
- Overconfident semantic matches.
- Graph edge interpreted as evidence rather than a locator.

Graph output is valuable when it reduces candidate count while preserving confirmation. It is harmful when it replaces confirmation.
