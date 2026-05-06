# Goal Recipe: Source Pipeline First Slice

## Destination

Produce the first safe slice of a source ingestion or normalization pipeline, with one source path working end to end through its intended first boundary.

The result should prove source identity, dry-run behavior, fixture behavior, output shape, and downstream non-mutation before expanding to additional sources or destinations.

## Phase Boundary

Stop after the first source path and its first durable boundary are verified.

Do not expand into multi-source routing, subscriber ingestion, knowledge-base writes, publishing, notifications, dashboards, or production scheduling unless explicitly asked in a later goal.

## Allowed Surface

- The source connector, parser, normalizer, or importer files named by the user.
- Fixture files or sample inputs needed to test the first source path.
- Tests covering source identity, dry-run behavior, fixture behavior, output shape, and downstream non-mutation.
- Local docs or reports that describe the first-slice contract.

## Forbidden Surface

- Secrets, cookies, auth stores, production credentials, and live tokens.
- Scheduler, deploy, notification, publishing, or bot-runtime changes.
- Downstream writes outside the first boundary.
- Broad cleanup, unrelated refactors, and additional source support.
- Vendor or generated files.

## Context Loading

Inspect before edits:

- existing source models and source identifiers
- current fixture shapes and documented sample inputs
- dry-run flags and where they are enforced
- downstream write paths that must remain untouched
- existing tests around ingestion, deduplication, and reporting
- public docs or comments that describe output fields

## Implementation Contract

Start with the smallest source path that can prove the boundary.

Prefer real parsers, structured data APIs, and existing local helpers over ad hoc string manipulation. Keep output fields either backed by real data or explicitly labeled as design-only.

Do not mark complete until the same contract is checked for fixture and live-style paths, even if the live path is mocked or blocked by missing credentials.

## Board

```text
Task ID: T001
Type: scout
Status: active
Objective: Map the first source path, source identity rules, dry-run behavior, fixture shapes, and downstream mutation risks.
Allowed files:
Verification:
Stop if: Required files are outside the allowed surface.
Receipt:

Task ID: T002
Type: worker
Status: queued
Objective: Implement the smallest first-slice change selected after T001.
Allowed files:
Verification:
Stop if: The slice needs new destinations, scheduler changes, secrets, or production access.
Receipt:

Task ID: T003
Type: audit
Status: queued
Objective: Run robustness probes and map every requirement to artifact evidence.
Allowed files:
Verification:
Stop if: Any requirement is unverified or only covered by proxy evidence.
Receipt:
```

## Robustness Probes

Always check:

- Existing row/source collision semantics.
- Fixture mode supports documented shapes.
- Dry-run flags affect both live and fixture paths.
- Output fields are real data or labeled design-only.
- Downstream mutation is negatively tested.
- Access coverage is split into fetched, inferred, and blocked.

Add project-specific probes for:

- duplicate source identifiers
- partial source access
- missing optional fields
- malformed fixture records
- empty source results
- retry or resume behavior

## Done Evidence

Provide:

- changed files
- tests or checks run
- fixture-path result
- live-style or blocked-live result
- dry-run proof for fixture and live-style paths
- negative proof that downstream mutation did not happen
- source access coverage split into fetched, inferred, and blocked
- output fields classified as real data or design-only

## Receipt

At completion or block, record:

```text
Changed:
Verified:
Robustness probes:
Fetched:
Inferred:
Blocked:
Not changed:
Remaining risk:
Next goal:
```

## Completion Audit

Before marking complete:

1. Restate the requested first-slice boundary.
2. List every allowed and forbidden surface.
3. Map each robustness probe to concrete evidence.
4. Map each done-evidence item to a command, test, file, report, or explicit blocker.
5. Confirm no downstream mutation happened outside scope.
6. Confirm every missing live dependency is labeled blocked rather than silently inferred.

If any item is missing, incomplete, weakly verified, or uncovered, keep working or mark the exact blocker with a receipt.
