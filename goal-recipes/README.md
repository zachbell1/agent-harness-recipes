# Goal Recipes

These are bounded task briefs for agent tools that support goal mode, long-running tasks, or structured work sessions.

Use this target schema when creating a new recipe from scratch or migrating an existing recipe:

- **Destination:** what should exist when the goal is done
- **Phase boundary:** where this goal stops, and what belongs to a later goal
- **Allowed surface:** repos, files, APIs, commands, and data the goal may touch
- **Forbidden surface:** anything explicitly out of scope
- **Context loading:** what to inspect before edits
- **Context Check Gate:** phase-boundary check before starting the next implementation slice
- **Implementation contract:** smallest safe slice first, with no broad cleanup
- **Board:** one active task, with queued scout/judge/worker/audit tasks only when useful
- **Robustness probes:** edge cases that would make the work look done while incomplete
- **Done evidence:** tests, commands, screenshots, reports, exact files, or live checks
- **Receipt:** what changed, what was verified, and what remains blocked
- **Completion audit:** map every requirement to concrete artifact evidence before marking complete

Good goal recipes are not autonomy spells. They are containers for supervised work with a clear finish line.

Existing recipes listed below may still use the lighter Destination / Source Context / Invariants / Done Evidence / Phase Boundary format until they are explicitly migrated.

## Context Check Gate

Before starting any new implementation slice or multi-step phase, run a short Context Check Gate.

The gate should include:

- a rough remaining-context estimate
- repo, runtime, and open-work state from the current evidence
- the next proposed slice or phase boundary
- one recommendation: `continue`, `checkpoint only`, `$outro now`, or `start fresh next turn`

The gate is mandatory at phase transitions, after material commits, database mutations, runtime mutations, before cross-repo work, deploy work, review work, long-running work, and before starting a conceptually distinct next slice.

Do not fire the gate noisily for tiny answers, one-command checks, or simple clarifications.

## Recipes

| Recipe | Use when |
|---|---|
| `public-repo-extractor.md` | Turning private patterns into a public-safe starter repo. |
| `source-pipeline-first-slice.md` | Building the first safe slice of a source ingestion or normalization pipeline. |
| `branch-release-critic.md` | Reviewing a branch or repo candidate before publishing. |
| `docs-from-reality.md` | Rebuilding docs from actual repo behavior. |

## Board Discipline

For long or multi-step goals, keep a small board:

```text
Task ID:
Type: scout | judge | worker | audit
Status: queued | active | completed | blocked
Objective:
Allowed files:
Verification:
Stop if:
Receipt:
```

Rules:

- Exactly one task is active.
- Worker tasks should be narrow enough to verify in the same run.
- Blocked tasks need receipts, not vague explanations.
- Final audit cannot pass while a worker task is still active or queued.

## Receipt Location

For short goals, the final assistant response can be the receipt.

For goals that produce durable decisions, code changes, public docs, or future install criteria, also save the receipt in one durable place:

- a repo planning or session note, if the receipt belongs to a specific project
- a research note, if the receipt evaluates a workflow or decision
- a handoff note, if the next session must resume from it

If a memory system is available, capture a compact pointer to the durable receipt. Do not duplicate long receipts across many places.

## Robustness Probes

Robustness probes are mandatory. Write them before implementation starts.

A good probe names a way the goal could look complete while still being wrong. Examples:

- a fixture path passes, but the live path ignores the same flag
- a report field is populated with placeholder data
- a duplicate row silently overwrites the wrong source
- a dry-run still mutates downstream state
- a green test does not cover the actual acceptance criterion

## Completion Discipline

A goal is complete only when the done evidence exists. A listening server, a plausible diff, or a confident summary is not enough.

Before marking a goal complete, restate every explicit requirement and map it to concrete artifact evidence. If any requirement is missing, incomplete, weakly verified, or uncovered, keep working or mark the exact blocker with a receipt.
