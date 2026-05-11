---
name: subagent-gate
description: Use when considering delegation, parallel agents, worker isolation, or subagent result integration.
---

# Subagent Gate

Delegate only when the task can be bounded, parallel, and independently useful. Do not delegate the immediate blocker on the critical path. Do not ask multiple agents to inspect the same broad area unless disagreement testing is the point.

A delegated task must include:

```text
objective:
owned_scope:
excluded_scope:
required_output:
evidence_required:
maximum_report_shape:
```

Subagent reports should be short: findings, touched files if any, evidence locators, risks, and verification status. The parent remains responsible for final judgment, artifact alignment, and user-facing claims.

Load repo-root `references/subagent-economics.md` before launching or integrating delegated work.
