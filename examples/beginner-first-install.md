# Example: Beginner First Install

This example shows a first pass for someone who mostly works by talking to a coding agent.

The setup goal is intentionally small: install three starter habits into one project.

- scope control
- completion evidence
- session handoff

## Starting Point

You have a project like this:

```text
example-app/
  README.md
  package.json
  src/
```

There is no existing `AGENTS.md`.

## Prompt 1: Read-Only Audit

Paste:

```text
I want to improve how you work in this project using a small markdown-only recipe repo.

First, audit my current project setup. Do not change anything.

Look for project-level instruction files such as AGENTS.md, CLAUDE.md, .cursorrules, README.md, docs/agent-notes.md, or similar files.

Do not read secrets, auth files, session logs, private memory databases, cookies, token stores, or unrelated personal files.

Report what instruction files you found, what rules already affect coding behavior, what verification expectations exist, what handoff expectations exist, and the safest place to add a small project-local rule.
```

Expected useful output:

```text
Current Setup
- Found README.md.
- No AGENTS.md, CLAUDE.md, .cursorrules, or docs/agent-notes.md found.
- README has setup commands but no agent behavior rules.

Potential Gaps
- No explicit scope boundary rule.
- No completion-evidence rule.
- No handoff rule.

Do Not Touch
- Secrets, auth files, hooks, global settings, generated logs, databases.

Safest install target
- Create AGENTS.md in the repo root.
```

If the agent does not name files it read, ask it to redo the audit from actual files.

## Prompt 2: Starter Bundle Plan

First make sure the agent can read:

- `rules/scoped-execution-lite.md`
- `rules/verification-lite.md`
- `rules/handoff-lite.md`

If it cannot read this repo from the project, paste those three files into the chat before asking for the plan.

Then paste:

```text
Now compare my current setup against this starter bundle:

- scoped-execution-lite: stay inside the requested repo, files, and phase
- verification-lite: do not claim work is complete without fresh evidence
- handoff-lite: end useful work with current state, verification, open items, and next action

Before editing anything:
1. Read the actual starter rule files, or tell me which rule file contents you need me to paste.
2. Tell me whether each item is NEW, UPGRADE, DUPLICATE, CONFLICT, or SKIP.
3. Recommend the smallest project-local install.
4. List every target file you would edit or create.
5. Explain how to remove the change later.
6. Explain how we will verify the behavior changed.

Do not edit anything yet.
```

Expected useful output:

```text
Plan
- verification-lite: NEW
- scoped-execution-lite: NEW
- handoff-lite: NEW

Recommended install
- Create AGENTS.md with a short Agent Operating Rules section.

Target files
- AGENTS.md

Removal
- Delete AGENTS.md, or remove the Agent Operating Rules section if the file later gains other content.

Verification
- Ask for a read-only task and confirm no edits happen.
- Ask "are we done?" and confirm the agent cites evidence or says what is unverified.
- Ask for a handoff and confirm it includes current state, verification, open items, and next action.
```

## Prompt 3: Approve The Edit

Paste:

```text
Install only the starter bundle you proposed.

Rules:
- Edit only AGENTS.md.
- Do not edit secrets, auth files, hooks, MCP configs, global settings, shell profiles, session logs, databases, or unrelated project files.
- After editing, show me the changed files and a diff summary.
- Then run or describe the verification checks.
```

Expected useful output:

```text
Changed files
- AGENTS.md

Diff summary
- Added project-local scope, verification, and handoff rules.

Verification
- Confirmed only AGENTS.md changed.
- Next behavioral checks: read-only boundary check, completion check, handoff check.
```

## Example Starter `AGENTS.md`

````markdown
# Agent Instructions

Use these instructions for this repo only.

## Scope

- Stay inside this repository unless explicitly asked otherwise.
- Before editing, identify the target repo, target files or directories, allowed phase, explicit exclusions, and expected verification.
- If the request is read-only, do not edit files.
- If the user names exact files, treat those files as the boundary unless the user expands it.
- Do not edit secrets, auth files, hooks, MCP configs, global settings, session logs, databases, or generated runtime state.
- Prefer the smallest change that satisfies the request.
- Do not opportunistically refactor unrelated code.
- Do not clean unrelated dirty files.
- If you discover a separate issue, report it as a follow-up instead of fixing it silently.
- When scope is ambiguous, make a conservative assumption and state it.
- Ask a question only when a wrong assumption could cause data loss, secret exposure, broad config changes, or edits outside the intended repo.

## Verification

- Do not claim work is complete without fresh evidence.
- Use tests, builds, lint checks, file checks, screenshots, manual checklists, or explicit blockers as evidence.
- If verification cannot be run, say what is unverified and name the next proof step.
- Do not use "should work," "looks good," or a partial check for a broader claim as proof.
- For tasks with a written spec, map each requirement to an artifact before claiming done.

Use this completion format:

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

## Handoff

End substantial work with:

- current branch or repo state
- changed files
- what was completed
- verification evidence
- what remains open
- blockers
- exact next action
- commands worth rerunning
- anything intentionally excluded

Keep open items honest. Include an open item only if it was started but not finished, blocked the current work, is an explicit follow-up, or must happen before the next phase.

Pickup note template:

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
````

## Prompt 4: Behavior Checks

Paste these one at a time:

```text
Boundary check: only inspect README.md and tell me what you would change. Do not edit.
```

```text
Completion check: are we done? Cite fresh evidence, or say what is not verified.
```

```text
Handoff check: end this session with current state, verification, open items, next action, and anything intentionally left untouched.
```

If those checks work, the first install succeeded.
