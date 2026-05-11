---
name: evidence-ledger
description: Use when claims, sources, gaps, corrections, or durable research state must be recorded without carrying raw transcripts forward.
---

# Evidence Ledger

Record evidence as compact claim rows, not as full source dumps. Each row must distinguish direct evidence, synthesis, inference, and unresolved uncertainty.

Use this row shape:

```text
claim:
status: verified | inferred | disputed | stale-risk | unsupported
evidence:
source_type:
source_date:
access_date:
locator:
confidence:
gap_or_correction:
```

When a later source changes the conclusion, add a correction row instead of silently replacing the old one. If the task produces a public artifact, ensure the artifact cites the canonical claim row rather than a transient chat summary.

Load repo-root `references/source-fidelity-rubric.md` for claim confidence and source hierarchy. Load repo-root `references/validation-and-release-gates.md` before publishing a bundle or report.
