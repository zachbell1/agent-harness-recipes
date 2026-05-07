# Harness Adapters

Adapters translate the canonical patterns in this repo into the instruction surface used by a specific AI coding harness.

Use adapters after running a setup scan. Do not start by copying these files into a project.

## Adapter Workflow

1. Run `prompts/setup-scanner.md`.
2. Identify the user's active harness surface.
3. Pick the matching adapter.
4. Classify each proposed behavior as `NEW`, `UPGRADE`, `DUPLICATE`, `CONFLICT`, or `SKIP`.
5. Propose the smallest project-local install.
6. Ask for approval before edits.
7. Verify behavior changed.
8. Record the removal path.

## Current Adapters

| Adapter | Use when |
|---|---|
| `agents-md.md` | The project uses or can use a repo-root `AGENTS.md`. |
| `codex.md` | The user wants Codex CLI or Codex app sessions to use this operating layer. |
| `claude-code.md` | The user wants Claude Code to use this operating layer. |
| `cursor.md` | The user wants Cursor rules to use this operating layer. |

## Universal Install Order

For a first install, prefer this order:

1. scoped execution
2. verification before completion claims
3. handoff/session continuity
4. setup scanner
5. goal brief workflow
6. release critic

Do not start with hooks, MCP configs, generated skills, global trust settings, auth setup, or automation.

## Adapter Boundaries

Adapters may describe:

- target instruction files
- what to install first
- how to preserve existing instructions
- behavior checks
- removal paths

Adapters must not include:

- real secrets
- private paths
- live MCP config
- hook scripts
- global trust settings
- generated runtime state
- one-step overwrite installers

If a tool supports advanced surfaces such as hooks, skills, memory, or MCP, adapter docs may mention them as later phases. They should not make them part of the beginner install.
