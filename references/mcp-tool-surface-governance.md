# MCP and Tool Surface Governance

Tool schemas are part of the context supply chain. A broad tool surface can increase hidden instruction load, increase accidental calls, and produce oversized outputs. Keep available tools aligned with the active task.

## Selection Rules

Use a tool only when it can answer a concrete question or perform a required action. Prefer local search for local files, official APIs for structured remote data, and direct repository tools for GitHub metadata. Avoid using a general web search when an official source URL or local file is already known.

## Output Rules

Ask tools for the smallest useful result. Prefer metadata, filenames, line windows, status summaries, and filtered records. For large result sets, fetch counts and top candidates first, then expand only the candidate that matters.

## Zero-Call Tools

Some available tools should remain unused in a run. Their mere availability does not justify a call. Record omitted tool families when their omission is relevant to a measurement run.

## Governance Record

```text
task_class:
tool_family_used:
reason:
expected_output_size:
actual_output_size:
slice_applied:
omitted_tool_family:
omission_reason:
```
