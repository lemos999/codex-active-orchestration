# Subagent Economics

Subagents are useful when they isolate context, run in parallel, or own disjoint implementation scopes. They are not automatically cheaper. Each subagent has startup instructions, task briefing, source reads, and report tokens. Use them when that overhead buys independence or parallel evidence.

## Good Delegation

- Independent code areas with disjoint write scopes.
- Parallel source checks for different claims.
- Verification tasks that can run while the parent implements.
- Bounded exploration with a concrete question and report shape.

## Poor Delegation

- The next critical-path blocker.
- Vague repository exploration.
- Duplicate inspection of the same files.
- Tasks requiring continuous parent judgment.
- Delegation used only to appear thorough.

## Report Contract

```text
finding:
evidence_locator:
files_changed:
verification:
risk:
open_question:
```

The parent should integrate reports by evidence, not by trust in the subagent. If a report lacks locators or quality status, ask for the missing data or treat it as weak evidence.
