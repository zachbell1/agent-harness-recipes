# Adapter: AGENTS.md

Use this adapter when a project uses, or can safely add, a repo-root `AGENTS.md`.

`AGENTS.md` is the most portable first target because many coding agents can read repository-level instructions, and the file is easy for a human to inspect.

## Good First Install

Install the starter bundle into a repo-root `AGENTS.md`:

- `rules/scoped-execution-lite.md`
- `rules/verification-lite.md`
- `rules/handoff-lite.md`

If `AGENTS.md` already exists, preserve the current content and add the smallest clear section.

If another instruction file already governs the project, classify `AGENTS.md` as `NEW`, `UPGRADE`, `DUPLICATE`, `CONFLICT`, or `SKIP` before recommending it.

## Setup Scan Targets

Safe files to inspect:

- `AGENTS.md`
- nested `AGENTS.md` files, if present
- `README.md`
- project docs that mention agent workflow, tests, release, or handoff
- package metadata only when needed to discover verification commands

Do not inspect secrets, auth files, logs, memory stores, hooks, MCP configs, or global settings unless the user explicitly approves a specific file.

## Install Shape

Use a short section like this:

```markdown
## Agent Operating Rules

- Stay inside the requested repo, files, and phase. If scope is ambiguous, ask before editing.
- Do not claim work is complete without fresh evidence such as a test, build, diff check, file check, screenshot, or explicit blocker.
- End substantial work with current state, changed files, verification, open items, and next action.
```

Keep the section boring. Do not paste every prompt in this repo into `AGENTS.md`.

## Verification

After install, run behavior checks:

```text
Boundary check: only inspect README.md and tell me what you would change. Do not edit.
```

```text
Completion check: are we done? Cite fresh evidence, or say what is not verified.
```

```text
Handoff check: end this session with current state, verification, open items, next action, and anything intentionally left untouched.
```

Expected result: the agent should respect read-only scope, cite evidence, and produce a useful handoff.

## Removal

Remove the added `Agent Operating Rules` section or restore the backup of `AGENTS.md`.

Start a fresh agent session and ask it to summarize current project instructions. The removed rules should no longer appear.

## Later Phases

Only after the starter bundle works, consider adding:

- a pointer to `prompts/setup-scanner.md`
- a pointer to `goal-recipes/README.md` for longer work
- a release-review instruction that points to `prompts/branch-release-critic.md`

Keep later additions explicit and reviewable.
