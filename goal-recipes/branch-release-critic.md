# Goal Recipe: Branch Release Critic

## Destination

Produce a release-readiness verdict for a branch, tag, or public repo candidate.

## Source Context

Inspect:

- git status and diff
- intended base branch
- README, install docs, security docs
- changed files
- tests or verification evidence
- generated/runtime-looking files

## Invariants

- Review first; do not fix unless asked.
- Findings come before summary.
- Do not invent issues to sound useful.
- Distinguish confirmed defects from open decisions.
- Treat secrets, auth material, logs, sessions, databases, and private paths as release blockers.

## Done Evidence

- findings ordered by severity
- release verdict: READY, READY_WITH_NOTES, or NOT_READY
- claim-accuracy check
- install/readiness check
- security check
- list of open decisions

## Phase Boundary

Stop at the verdict. Do not merge, tag, push, publish, or create a release unless explicitly asked.
