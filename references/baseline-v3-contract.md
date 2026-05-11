# Baseline V3 Contract

Baseline v3 records token usage and quality outcomes without preserving raw prompt text. It exists to answer one question: did a specific context intervention reduce tokens for a comparable task while preserving quality?

## Required Fields

```text
run_id:
timestamp_local:
timestamp_utc:
timezone:
task_class:
task_fingerprint:
repository_or_dataset:
model:
runtime:
tool_surface:
active_root_contract:
active_skills:
active_references:
intervention_label:
input_tokens:
cached_input_tokens:
output_tokens:
total_tokens:
quality_gate:
quality_result:
failure_or_regression:
notes:
```

`task_fingerprint` should identify the task without storing private content. Use a stable label, hash, issue number, benchmark ID, or manually written descriptor.

## Comparability

Compare runs only when task class, model family, repository state, tool surface, and required quality gates are comparable. If a run omits tests, citations, or review depth required by the baseline, it is not a clean savings win.

## Intervention Labels

Use explicit labels:

```text
baseline
output_slicing
context_router
skill_progressive_disclosure
mcp_surface_reduction
subagent_isolation
graph_locator_prefilter
compact_root_contract
combined_intervention
```

## Interpretation

Input-token reduction suggests better context supply. Output-token reduction is useful only when the answer remains complete. Cached input tokens affect cost and latency interpretation but should not be counted as context removed. Total tokens are useful for user-facing cost comparison, but diagnose input and output separately.
