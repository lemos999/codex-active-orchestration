---
name: coding-operation-loop
description: Use when implementing, repairing, refactoring, testing, reviewing for fixes, setup, or executing an approved coding plan with minimal context waste.
---

# Coding Operation Loop

Run in order unless task is a direct command. Weight: `tiny` silent/brief, `standard` normal, `heavy` may add durable plan or evidence.

```text
understand -> locate -> inspect -> scope -> patch -> verify -> repair -> report
```

Understand behavior and success condition. Locate candidates with fast search, file lists, tests, symbols, or graph locators before broad content. Inspect only owners, relevant tests, config, conventions. Scope writes narrowly. Patch in style. Verify with the cheapest meaningful command. Repair only observed failures or clear omissions. Report changed files, behavior, verification.

Invoking this loop counts as using `coding-operation-loop` even if this file was not opened. Do not report `0 skills` or `none` after saying the loop handled work. If only a similar tactic was followed without route/invocation, do not claim the skill. Keep opened skill files separate from used skills.

Broad explanation prompts like `Explain this codebase` are not coding just because the target is a repo. Send through `context-router` first to narrow explanation scope; enter this loop only for implementation, repair, tests, review fixes, or setup.

For `tiny`, skip durable plan files, broad ledgers, refs unless required. For `heavy`, load repo-root `references/coding-operating-structure.md` and preserve resume/audit reasoning.

Use `output-slicing` for large command output. Use `source-fidelity` when external API behavior, package versions, or current docs affect code. Use `baseline-observer` for token/workflow comparisons. Use `subagent-gate` only when independent parallel work is justified.

Load repo-root `references/coding-operating-structure.md` only when broad, risky, multi-file, or durable planning is needed.
