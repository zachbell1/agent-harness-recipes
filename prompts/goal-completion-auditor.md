# Prompt: Goal Completion Auditor

Use before claiming a goal, long-running task, or implementation slice is complete.

```text
Audit whether this goal is actually complete.

Do not rely on confidence, effort, a plausible diff, passing tests, a green manifest, a listening server, or memory of earlier work as completion proof by itself.

Build a prompt-to-artifact checklist:

1. Restate the original objective as concrete deliverables or success criteria.
2. List every explicit requirement, named file, numbered item, command, test, gate, and deliverable.
3. For each item, cite concrete evidence:
   - file changed
   - command output
   - test result
   - screenshot
   - report
   - live check
   - explicit blocker
4. Verify that each test, manifest, verifier, or green status actually covers the requirement it is being used for.
5. Identify any requirement that is missing, incomplete, weakly verified, or uncovered.
6. Confirm forbidden surfaces were not touched.
7. Confirm queued or active worker tasks are completed, blocked with receipts, or moved into a later goal.

Output:

- Completion verdict: COMPLETE, INCOMPLETE, or BLOCKED.
- Requirement-to-evidence checklist.
- Missing or weak evidence.
- Forbidden-surface check.
- Remaining tasks or next goal.

Only call the goal complete when every requirement is backed by concrete artifact evidence and no required work remains.
```
