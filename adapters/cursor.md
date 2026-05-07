# Adapter: Cursor

Use this adapter when the user wants Cursor to follow the operating layer in this repo.

Cursor projects may use repo-level instructions, `.cursorrules`, or files under `.cursor/rules`. The exact target should come from the setup scan, not a guess.

## Good First Install

Prefer the current project-local Cursor instruction surface if it exists.

Common targets:

- `AGENTS.md`, if the project already uses it or the user wants a cross-agent file
- `.cursorrules`, if the project already uses it
- `.cursor/rules/*.md`, if the project already uses Cursor rules

Install the starter bundle:

- scoped execution
- verification before completion claims
- handoff/session continuity

Do not create multiple rule surfaces at once. Pick one target and verify it.

## Setup Scan Targets

Safe project-local targets:

- `AGENTS.md`
- `.cursorrules`
- `.cursor/rules/`
- README and workflow docs
- project-local rule files
- package metadata only when needed to identify verification commands

Do not inspect or edit:

- secrets
- auth stores
- browser profiles
- session logs
- memory databases
- MCP configs
- hooks
- global settings
- unrelated personal files

## Install Shape

Use a short rule section:

```markdown
# Agent Operating Rules

- Stay inside the requested repo, files, and phase. Ask before widening scope.
- Do not claim completion without fresh evidence from a test, build, diff check, file check, screenshot, or explicit blocker.
- End substantial work with current state, changed files, verification, open items, and next action.
```

If adding a file under `.cursor/rules/`, use the repo's existing rule naming pattern if one exists. If no pattern exists, propose the filename before creating it.

## Verification

After install, start a fresh Cursor agent interaction in the target project and ask:

```text
Boundary check: inspect README.md only. Do not edit. Tell me what you would change and cite the instruction rule you are following.
```

```text
Completion check: are we done? Cite fresh evidence, or say what is not verified.
```

```text
Handoff check: end this session with current state, verification, open items, next action, and anything intentionally left untouched.
```

Expected result: Cursor respects the boundary, cites evidence, and leaves a usable handoff.

## Removal

Remove the added section or delete the added Cursor rule file.

Start a fresh Cursor interaction and ask it to summarize active project rules. The removed behavior should not appear unless another rule duplicates it.

## Later Phases

Later Cursor adapter docs may cover:

- task oriented rules
- goal workflow pointers
- release-review prompts
- update-check prompts

Keep the first install small. Cursor rule sprawl makes behavior harder to debug.
