# Prompt: Goal Brief Builder

Use before starting a long-running goal, implementation slice, audit pass, or structured agent work session.

```text
Turn this request into a goal brief before editing anything.

Build the brief with these sections:

1. Destination
   - What should exist when the goal is done.

2. Phase boundary
   - Where this goal stops.
   - What belongs to a later goal.

3. Allowed surface
   - Repos, files, APIs, commands, and data the goal may touch.

4. Forbidden surface
   - Anything explicitly out of scope.

5. Context loading
   - What you will inspect before edits.

6. Implementation contract
   - Smallest safe slice first.
   - No broad cleanup.
   - No adjacent feature work unless explicitly required.

7. Board
   - Create a small task board with exactly one active task.
   - Use scout, judge, worker, or audit tasks only where useful.

8. Robustness probes
   - Name the edge cases that could make the work look done while incomplete.

9. Done evidence
   - Commands, tests, screenshots, reports, exact files, live checks, or explicit blockers.

10. Receipt format
   - What changed.
   - What was verified.
   - What remains blocked.

11. Completion audit
   - How every requirement will be mapped to concrete artifact evidence before marking complete.

After drafting the brief, pause for approval if the allowed surface, forbidden surface, or phase boundary is ambiguous. If the user asked for execution and the scope is clear, proceed with the first active task only.
```
