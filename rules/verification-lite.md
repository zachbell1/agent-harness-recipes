# Rule: Verification Lite

Do not claim work is complete without fresh evidence.

## Before A Completion Claim

Identify what would prove the claim:

- test command
- build command
- linter/typecheck
- curl or UI check
- file tree check
- requirements checklist
- manual review checklist

Then run or perform that proof in the current session. If you cannot run it, say exactly why and mark the claim unverified.

## Completion Claim Format

Use:

```text
Status: verified
Evidence: <command/checklist and result>
Remaining risk: <anything not covered>
```

Or:

```text
Status: not fully verified
Blocked verification: <what could not be run>
Known evidence: <what was checked>
Next proof step: <specific command or check>
```

## Red Flags

Do not use these as proof:

- "should work"
- "looks good"
- "I think"
- previous session output
- a partial check for a broader claim
- a passing test that does not cover the changed behavior

## Requirements Checklist

For tasks with a written spec, map each requirement to an artifact before claiming done.
