# Validation and Release Gates

Before releasing or adopting a Token Context OS bundle, run structural, safety, evidence, and measurement checks.

## Structural Gate

- `AGENTS.md` exists at the intended root.
- Every skill lives in `skills/<name>/SKILL.md`.
- Every skill has YAML frontmatter with `name` and `description`.
- Skill names match directory names.
- References named by skills exist.
- No unrelated archives, transcripts, credentials, or private prompts are included.

## Evidence Gate

- Current claims cite inspected evidence or are marked as inference.
- Volatile claims have dates.
- Corrections remain visible.
- Public artifacts can be traced to canonical claim rows.

## Measurement Gate

- Savings claims have comparable baseline and intervention rows.
- Input, cached input, output, and total tokens are separated.
- Quality gates passed.
- Tool surface and active skills are recorded.
- Failed or weaker outputs are excluded from savings claims.

## Context Budget Gate

- The root contract has an explicit approximate-token budget.
- Skills remain short enough to load on demand.
- References can be measured separately from the always-on root.
- Approximate text counts are treated as preflight data, not real runtime savings.

## Release Statement

A release should say what the bundle is, what it is not, what was validated, and what still requires local measurement. Avoid universal performance claims unless supported by broad, reproducible evidence.
