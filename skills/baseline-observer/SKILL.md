---
name: baseline-observer
description: Use when measuring token usage, preparing comparable baseline rows, evaluating an intervention, or making any efficiency claim.
---

# Baseline Observer

No numerical savings claim is valid without comparable baseline and intervention rows. Record task class, environment, model, tool state, prompt surface, intervention label, token fields, and quality outcome. Do not store raw private prompt text or sensitive transcript content in the baseline row.

Minimum row:

```text
run_id:
timestamp_local:
timestamp_utc:
task_class:
model:
runtime:
repo_or_dataset:
intervention_label:
input_tokens:
cached_input_tokens:
output_tokens:
total_tokens:
quality_gate:
notes:
```

Compare like with like. A shorter answer, failed test, missing citation, or weaker review is not a valid token win. Prompt caching may be recorded separately, but cached tokens do not prove the context was smaller.

Load repo-root `references/baseline-v3-contract.md` before creating or changing baseline records.
