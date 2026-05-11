# Compact Prompt Composition

Compact prompt composition writes instructions that are short because they are well-routed, not because they omit obligations. The goal is a smaller active context with the same or better execution fidelity.

## Root Layer

The root layer should contain durable authority, task classification, safety boundaries, context discipline, skill routing, and final answer expectations. It should not repeat detailed procedures that can live in skills or references.

## Skill Layer

A skill should have a precise trigger, a short procedure, a small output contract, and named references for deeper detail. The skill should be executable after one read. If a skill needs many examples, move examples to a reference and keep the skill as a gateway.

## Reference Layer

References carry detailed rubrics, schemas, checklists, and examples. They should be stable, focused, and named from the skill that loads them.

## Compression Moves

Use one general rule instead of repeated near-duplicates. Use concrete behavior instead of motivational phrasing. Bind output by naming fields, artifacts, verification checks, and forbidden omissions. Turn broad negative warnings into positive operating requirements plus a clear boundary. Keep uncertainty explicit rather than hiding it behind confident brevity.

## Quality Test

An instruction rewrite passes only if:

- A new agent can identify when to use it.
- Required outputs are still explicit.
- Safety and evidence obligations remain visible.
- The root context is smaller or more routable.
- The rewrite does not depend on private examples or hidden terminology.
