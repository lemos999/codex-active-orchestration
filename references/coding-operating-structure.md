# Coding Operating Structure

Efficient coding agents do not read the whole repository first. They find the code that owns the requested behavior, change the smallest coherent surface, and verify the highest-risk path. The goal is correct engineering progress per active context token.

## Loop

```text
understand -> locate -> inspect -> scope -> patch -> verify -> repair -> report
```

## Steps

Understand only what implementation needs. Classify the task: bug fix, feature, refactor, test, migration, setup, review repair, or direct command. Define the success signal before reading broadly.

Locate candidates with cheap signals: file lists, `rg`, test names, exported symbols, routes, manifests, errors, and graph candidates. Location should shrink the search set, not become a repository tour.

Inspect the smallest slices that explain behavior: imports, interfaces, target functions, callers, tests, config, and nearby patterns. If insufficient, expand by a named reason such as caller depth, fixture path, config path, or runtime entry point.

Scope writes to the files needed for the behavior. Preserve user edits and local style. Avoid unrelated cleanup. Add abstraction only when it removes real duplication or matches an established local pattern.

Patch in repository style: naming, formatting, errors, dependencies, and tests. Comments should explain non-obvious decisions, not narrate simple code.

Verify with the cheapest meaningful check: targeted test, typecheck, touched-file lint, build, or focused manual check. If unavailable, state the boundary and run the next best read-only check.

Repair observed failures without broadening the rewrite unless the failure proves scope was wrong. Rerun the relevant check and stop when the success condition is met.

Report changed files, behavioral result, verification command and outcome, and remaining risk. Do not paste raw logs unless requested.
