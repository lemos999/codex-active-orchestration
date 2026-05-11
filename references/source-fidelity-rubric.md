# Source Fidelity Rubric

Use the strongest source that is practical for the claim.

## Source Tiers

Tier 1: official documentation, standards, repository source, release notes, primary papers, direct datasets, legal or regulatory text, and first-party announcements.

Tier 2: maintainer comments, issue discussions, benchmark repositories, conference material, and technical blog posts with reproducible details.

Tier 3: news, summaries, forum posts, social posts, tutorials, and aggregator pages.

Tier 4: memory, uncited model knowledge, hearsay, and unsupported inference.

High-impact or current claims need Tier 1 or a clearly stated limitation. Tier 3 can orient the search but should not carry the final claim unless the task is about public reaction or commentary.

## Claim Status

```text
verified: directly supported by inspected evidence
inferred: reasonable synthesis from evidence, not directly stated
disputed: sources conflict or interpretation is contested
stale-risk: could have changed since inspection
unsupported: not enough evidence to rely on
```

## Correction Practice

When a claim changes, write a correction note with the old claim, new claim, evidence that caused the correction, and the artifact that must be updated. Do not silently erase the prior state if downstream users may have relied on it.
