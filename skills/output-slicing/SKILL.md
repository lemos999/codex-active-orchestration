---
name: output-slicing
description: Use when command output, logs, diffs, JSON, search results, or source files are too large to load whole.
---

# Output Slicing

Do not paste or load large output by default. Define the question the output must answer, then choose a slice strategy:

- Error slice: first failing command, stack frame, diagnostic code, and nearby lines.
- Diff slice: changed files, hunk headers, risky hunks, and public API changes.
- Search slice: exact matches with file paths and nearby context.
- JSON slice: schema keys, counts, selected rows, and anomalies.
- Source slice: imports, public interfaces, target function, callers, and tests.

Keep enough surrounding context to avoid false interpretation. If the first slice is insufficient, expand by one explicit criterion rather than dumping everything. Preserve file paths, line numbers, command names, timestamps, and exit codes when they matter.

Load repo-root `references/token-efficiency-playbook.md` for slicing patterns and repo-root `references/mcp-tool-surface-governance.md` when tool output shape is the source of bloat.
