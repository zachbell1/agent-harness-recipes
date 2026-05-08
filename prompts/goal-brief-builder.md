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
   - If using the shared workflow kernel or Agent Briefing Index for context, pass the current user request or concrete goal as `--topic` so advisor ranking responds to the active topic, not just the project slug.

6. Context Check Gate
   - Before starting a new implementation slice or multi-step phase, estimate remaining context roughly.
   - Summarize repo, runtime, and open-work state from current evidence.
   - Recommend one of: continue, checkpoint only, $outro now, or start fresh next turn.
   - Require the gate at phase transitions, after material commits/DB/runtime mutations, before cross-repo/deploy/review/long-running work, and before conceptually distinct next slices.
   - Skip the gate for tiny answers, one-command checks, or simple clarifications.

7. Implementation contract
   - Smallest safe slice first.
   - No broad cleanup.
   - No adjacent feature work unless explicitly required.
   - Advisor routing may rank candidates automatically, but advisor execution remains manual unless explicitly scoped later.

8. Board
   - Create a small task board with exactly one active task.
   - Use scout, judge, worker, or audit tasks only where useful.

9. Robustness probes
   - Name the edge cases that could make the work look done while incomplete.

10. Done evidence
   - Commands, tests, screenshots, reports, exact files, live checks, or explicit blockers.

11. Receipt format
   - What changed.
   - What was verified.
   - What remains blocked.

12. Completion audit
   - How every requirement will be mapped to concrete artifact evidence before marking complete.

After drafting the brief, pause for approval if the allowed surface, forbidden surface, or phase boundary is ambiguous. If the user asked for execution and the scope is clear, proceed with the first active task only.
```
