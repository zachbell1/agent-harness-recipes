# Start Here

Use this guide if your main interface is a coding agent such as Cursor, Claude Code, Codex CLI, or another model that can read and edit your project files.

The goal is not to install a whole harness. The goal is to give your agent three simple habits:

- stay inside the scope you gave it
- prove work before saying it is done
- leave a useful handoff when the session ends

## What You Need

- A project you can safely edit.
- A coding agent that can read files in that project.
- This repo available locally or open in a browser so you can copy prompts from it.
- About 10 minutes for the first setup pass.

Do not start by editing global settings, secrets, hooks, MCP configs, auth files, or shell profiles.

## The Beginner Path

### Step 1: Ask For A Read-Only Audit

Open your project in your coding agent and paste this:

```text
I want to improve how you work in this project using a small markdown-only recipe repo.

First, audit my current project setup. Do not change anything.

Look for project-level instruction files such as AGENTS.md, CLAUDE.md, .cursorrules, README.md, docs/agent-notes.md, or similar files.

Do not read secrets, auth files, session logs, private memory databases, cookies, token stores, or unrelated personal files.

Report:
1. What instruction files you found.
2. What rules already affect your coding behavior.
3. What verification rules already exist.
4. What handoff or session-continuity rules already exist.
5. What security boundaries already exist.
6. A short "Do Not Touch" list.
7. The safest place to add a small project-local rule, if any.

Do not make an installation plan yet.
```

Good output should mention real files it read. If the agent only guesses, ask it to read the files first.

### Step 2: Ask For The Starter Bundle Plan

After the audit, make sure your agent can read these files:

- `rules/scoped-execution-lite.md`
- `rules/verification-lite.md`
- `rules/handoff-lite.md`

If the agent cannot read this repo from your project, paste the contents of those three files into the chat before asking it to plan the install.

Then paste this:

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

For most projects, the smallest install is either:

- create a project `AGENTS.md`, or
- append a short "Agent Operating Rules" section to an existing project instruction file.

### Step 3: Approve One Narrow Edit

If the plan looks safe, paste this:

```text
Install only the starter bundle you proposed.

Rules:
- Edit only the target files you listed.
- Do not edit secrets, auth files, hooks, MCP configs, global settings, shell profiles, session logs, databases, or unrelated project files.
- If an existing file will change, preserve the existing rules and add the smallest clear section.
- After editing, show me the changed files and a diff summary.
- Then run or describe the verification checks.
```

Stop if the agent tries to edit global config, auth files, hooks, or anything you did not approve.

### Step 4: Verify It Worked

Use one or two small checks:

```text
Boundary check: only inspect README.md and tell me what you would change. Do not edit.
```

Expected behavior: the agent should restate that this is read-only and avoid edits.

```text
Completion check: are we done? Cite fresh evidence, or say what is not verified.
```

Expected behavior: the agent should cite a command, file check, checklist, or explicit blocker instead of saying "looks good."

```text
Handoff check: end this session with current state, verification, open items, next action, and anything intentionally left untouched.
```

Expected behavior: the agent should produce a pickup note that a later session can use.

## What To Use Next

After the starter bundle works:

- Use `prompts/codebase-archaeologist.md` before editing an unfamiliar repo.
- Use `prompts/docs-from-reality.md` when docs are stale or vague.
- Use `prompts/branch-release-critic.md` before sharing or publishing a branch.
- Use `goal-recipes/README.md` for longer tasks that need a goal brief, board, robustness probes, and completion audit.

## Tiny Glossary

- **Agent:** the model-powered coding tool you talk to.
- **Project instruction file:** a file like `AGENTS.md`, `CLAUDE.md`, or `.cursorrules` that tells the agent how to behave in a repo.
- **Rule:** a short behavior instruction, such as "do not claim done without evidence."
- **Prompt:** text you paste into the agent for a specific task.
- **Verification:** fresh evidence that the work actually happened, such as a test, build, diff, file check, screenshot, or checklist.
- **Handoff:** the short end-of-session note that says what changed, what was checked, what remains open, and what to do next.
- **Goal brief:** a structured plan for longer work, including scope, forbidden areas, done evidence, and final audit.
- **MCP, hooks, global config:** advanced automation and tool wiring. Leave these alone during the beginner install.
