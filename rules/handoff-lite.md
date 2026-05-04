# Rule: Handoff Lite

End useful work with a pickup note that the next session can trust.

## Handoff Contents

Include:

- current branch or repo state
- files changed
- what was completed
- verification evidence
- what remains open
- blockers
- exact next action
- commands worth rerunning
- anything intentionally excluded

## Keep Open Items Honest

An open item belongs in the handoff if:

- it was started but not finished
- it blocked the current work
- it is an explicit follow-up from this session
- it must happen before the next phase can proceed

Do not add unrelated environmental noise just because you saw it.

## Pickup Note Template

```text
Summary:
- <one or two sentences>

Current state:
- Repo:
- Branch:
- Dirty files:

Completed:
- <item>

Verification:
- <command/check and result>

Open items:
- <item or "None">

Next action:
- <specific next step>

Do not forget:
- <scope boundary, risk, or exclusion>
```
