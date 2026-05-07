# Adapter: Codex

Use this adapter when the user wants Codex sessions to follow the operating layer in this repo.

Codex can read project instructions such as `AGENTS.md`. Some users may also maintain local skills or global instructions. The first install should still be project-local unless the user explicitly asks for a broader setup.

## Good First Install

Prefer a repo-root `AGENTS.md` using `adapters/agents-md.md`.

Install:

- scoped execution
- verification before completion claims
- handoff/session continuity

This gives Codex useful behavior without changing global Codex config, auth, MCP allowlists, review wrappers, or local skills.

## Setup Scan Targets

Safe project-local targets:

- `AGENTS.md`
- README and project workflow docs
- existing project-level instructions
- package metadata only when needed to identify verification commands

Optional user-approved targets:

- a local Codex skill that points to this repo
- a global instruction file that only references this repo by placeholder path

Do not inspect or edit:

- Codex auth state
- session logs
- runtime databases
- MCP configs
- review wrapper scripts
- trust settings
- secrets

## Optional Goal Pointer

For users who already use long-running Codex goals, a later phase may add a thin pointer:

```markdown
For long-running implementation slices, audit/docs passes, release-critic work, or source-pipeline first slices, use `<AGENT_HARNESS_RECIPES_DIR>/goal-recipes/README.md` before editing. Draft the goal brief, keep one active board task, run robustness probes, and finish with a completion audit.
```

Do not install this before the starter bundle is verified.

## Verification

After installing project-local rules, start a fresh Codex session in the target project and ask:

```text
Summarize the project instructions you are using. Then perform a read-only boundary check against README.md only.
```

Expected result:

- Codex mentions the project-local operating rules.
- It treats the task as read-only.
- It does not edit unrelated files.

For goal routing, use:

```text
Use the goal workflow for the next bounded docs pass. Draft the brief and board before editing.
```

Expected result: Codex drafts a Goal Brief + Board before edits.

## Removal

Remove the added project-local section or pointer.

Start a fresh Codex session and ask it to summarize active instructions. The removed behavior should not be present unless another instruction file duplicates it.

## Later Phases

Later Codex-specific work may document:

- local skill pointers
- review-only invocation patterns
- project pickup conventions
- safe update checks

Keep those separate from the beginner install.
