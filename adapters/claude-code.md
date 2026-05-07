# Adapter: Claude Code

Use this adapter when the user wants Claude Code to follow the operating layer in this repo.

Claude Code supports several advanced surfaces, including project instructions, skills, hooks, memory, and MCP. The first install should not touch all of them. Start with project-local instructions.

## Good First Install

Prefer one of these project-local targets:

- repo-root `AGENTS.md`
- an existing `CLAUDE.md`
- another existing project instruction file already used by the repo

Install the starter bundle:

- scoped execution
- verification before completion claims
- handoff/session continuity

Preserve existing instructions. Add the smallest section that creates the missing behavior.

## Setup Scan Targets

Safe project-local targets:

- `AGENTS.md`
- `CLAUDE.md`
- README and workflow docs
- project-local rule files
- package metadata only when needed to identify verification commands

Optional user-approved targets:

- specific Claude Code skill files
- specific hook definitions
- specific MCP config files

Do not inspect or edit:

- auth state
- secrets
- private memory
- session transcripts
- global trust settings
- browser profiles
- unrelated home-directory files

## Advanced Surfaces Are Later Phases

Claude Code can use skills, hooks, MCP, and memory. Those are powerful surfaces, but they are not the beginner install.

Treat them as separate phases:

- **Skills:** useful for packaging repeatable workflows after the markdown pattern is proven.
- **Hooks:** useful for enforcement or automation only after manual behavior is stable.
- **MCP:** useful for tool access, but expands data and permission boundaries.
- **Memory:** useful for continuity, but must not import private state into public examples.

Do not add hooks, MCP configs, or memory rules unless the user explicitly opens that phase.

## Verification

After install, start a fresh Claude Code session in the target project and ask:

```text
Summarize the project instructions you are using. Then inspect README.md only and do not edit.
```

Expected result:

- Claude Code cites project-local instructions.
- It keeps the task read-only.
- It does not widen scope.

For handoff behavior, ask:

```text
End this session with current state, verification, open items, next action, and anything intentionally left untouched.
```

Expected result: the handoff is specific enough for a later session to resume.

## Removal

Remove the added section from `AGENTS.md`, `CLAUDE.md`, or the target instruction file.

Start a fresh Claude Code session and ask it to summarize active project instructions. The removed rules should not appear unless duplicated elsewhere.

## Later Phases

Later Claude Code adapter docs may cover:

- a thin skill that points to `goal-recipes/README.md`
- a release-review workflow
- safe hook design
- MCP allowlist review
- memory boundaries

Keep each advanced surface separately approved and separately verified.
