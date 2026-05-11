# Token Efficiency Playbook

The first reliable token savings usually come from not loading irrelevant material. The practical order is:

1. Route the task before reading.
2. Locate candidate files, sources, or tools.
3. Slice output by question.
4. Expand only when the slice is insufficient.
5. Preserve evidence rows instead of raw transcripts.
6. Measure comparable baseline and intervention runs.

## Output Slicing Patterns

For logs, keep command, exit code, first failure, final summary, and nearby diagnostic lines. For diffs, keep changed filenames, public API changes, risky hunks, and tests. For source files, keep imports, symbols, target implementation, callers, and relevant tests. For JSON, keep schema, counts, anomalous rows, and selected examples. For search, keep exact matching lines with paths and line numbers.

## Relevance Gate

Before loading context, ask:

```text
What decision will this context change?
What smaller locator can answer first?
What evidence must be preserved if the context is discarded?
What quality gate could fail if this context is omitted?
```

If the answer is unclear, do not load the context yet. Search, summarize, or inspect a narrower slice.

## Prompt Caching

Prompt caching can lower effective cost or latency when stable prefixes repeat. It should be tracked separately from context minimization. A large cached prefix may still crowd the model's working window and may still hide irrelevant policy. Cache ratio is an accounting signal, not a quality signal.

## Savings Formula

For a comparable pair:

```text
input_delta_pct = (baseline_input - intervention_input) / baseline_input * 100
total_delta_pct = (baseline_total - intervention_total) / baseline_total * 100
```

Report the quality gate beside the delta. A failed or weaker output invalidates the efficiency claim.
