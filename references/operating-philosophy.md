# Operating Philosophy

Token Context OS treats an agent run as a context supply chain. The expensive object is not only the user's prompt. It is the combined surface of root instructions, skills, references, tool schemas, retrieved files, command output, source quotations, subagent reports, and final artifacts. A good operating contract reduces irrelevant supply while preserving the evidence needed to act correctly.

The root `AGENTS.md` should therefore be a constitution and router. It should say how to classify work, how authority is resolved, what cannot be sacrificed, and which skill to load. It should not contain every detailed workflow. Skill files should be short procedural handles. Reference files should hold deeper policy and examples that are only read when needed.

The system favors measured reduction over aesthetic brevity. A shorter instruction that creates ambiguity, causes extra tool calls, or loses evidence is not efficient. A longer reference that stays unloaded until needed can be cheaper than a bloated root file. The relevant unit is the active context consumed by a task class at runtime.

Core rules:

1. Put durable routing in the root.
2. Put active procedures in skills.
3. Put deep detail in references.
4. Put evidence in ledgers or artifacts, not in repeated chat summaries.
5. Put numerical savings behind comparable measurements.

Correctness has priority over token reduction. Tests, primary evidence, safety constraints, and source provenance are not waste. Waste is irrelevant repetition, broad raw output, stale context, premature delegation, unneeded tool schemas, and unverified summaries.
