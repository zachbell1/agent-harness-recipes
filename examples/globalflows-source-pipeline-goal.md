# Example: Public Source Pipeline First Slice

This example shows how to use `goal-recipes/source-pipeline-first-slice.md` for a public research source without exposing private decision systems, credentials, subscriber data, or local machine paths.

Replace the names and paths with your own project placeholders before use.

## Goal Brief

### Destination

Implement the first safe slice for ingesting one public research source into a local source pipeline.

The slice should normalize one source record shape, preserve source identity, support fixture mode, respect dry-run behavior, and produce a receipt that separates fetched, inferred, and blocked access.

### Phase Boundary

Stop after one source path reaches the first local boundary.

Do not add downstream knowledge-base writes, private decision logic, subscriber-only access, notifications, scheduling, dashboards, or multi-source routing in this goal.

### Allowed Surface

- `<PROJECT_DIR>/src/sources/<source_name>.*`
- `<PROJECT_DIR>/src/pipeline/source_normalizer.*`
- `<PROJECT_DIR>/tests/fixtures/<source_name>/`
- `<PROJECT_DIR>/tests/test_<source_name>_source_pipeline.*`
- `<PROJECT_DIR>/docs/source-pipeline-first-slice.md`

### Forbidden Surface

- secrets, cookies, credentials, tokens, or browser auth state
- production schedulers or deployment config
- private decision, execution, or alerting code
- downstream database writes beyond the first local boundary
- unrelated parser or source refactors

### Context Loading

Inspect:

- existing source identifiers
- fixture format conventions
- dry-run flag behavior
- first-boundary data model
- downstream write paths that must not run
- tests for dedupe, collision, and reporting

### Implementation Contract

Implement one public-source path only.

Use fixtures for repeatable verification. If live access is unavailable or intentionally out of scope, label it blocked instead of pretending fixture coverage proves live access.

### Board

```text
Task ID: T001
Type: scout
Status: active
Objective: Map source identity, fixture shape, dry-run behavior, first boundary, and mutation risks.
Allowed files: read-only across the allowed surface
Verification: source map and first-slice risk list
Stop if: source requires credentials or private access
Receipt:

Task ID: T002
Type: worker
Status: queued
Objective: Implement the first source path and focused tests.
Allowed files: source file, normalizer, fixtures, focused tests, first-slice docs
Verification: focused test command and dry-run check
Stop if: implementation requires downstream writes or additional sources
Receipt:

Task ID: T003
Type: audit
Status: queued
Objective: Run source-pipeline robustness probes and completion audit.
Allowed files: changed files and test output
Verification: requirement-to-evidence checklist
Stop if: any robustness probe lacks evidence
Receipt:
```

### Robustness Probes

- Existing row/source collision semantics are covered by a focused test.
- Fixture mode supports every documented fixture shape.
- Dry-run flags affect both live-style and fixture paths.
- Output fields are real source data or labeled design-only.
- Downstream mutation is negatively tested.
- Access coverage is split into fetched, inferred, and blocked.

### Done Evidence

- changed files list
- fixture test command and result
- dry-run command or focused check and result
- negative downstream mutation test
- source access receipt:
  - fetched:
  - inferred:
  - blocked:
- output field classification:
  - real data:
  - design-only:

### Receipt

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

### Completion Audit

Before calling this complete, map every item in the goal brief to concrete evidence.

If live access, downstream writes, or production scheduling are not part of the evidence, mark them out of scope or blocked. Do not imply that fixture success proves more than it actually proves.
