# Agent Harness Recipes

Markdown-first recipes for improving AI coding and agent harness setups without importing someone else's private machine.

This repo is for people who already use tools like Claude Code, Codex CLI, Cursor, or another agentic coding assistant and want a safer operating layer:

- better setup audits before installing anything
- reusable goal prompts for bounded work
- lightweight `AGENTS.md` patterns
- verification rules that prevent "done" without proof
- handoff notes that make the next session easier
- release review prompts before publishing a branch

It intentionally starts as plain markdown. There are no scripts, hooks, MCP configs, installers, generated skills, runtime state, or live automation in v1.

## Start Here

If you mostly interact with code by talking to a model, start with `START_HERE.md`.

That guide gives you an exact first-run flow:

1. Ask your agent for a read-only audit.
2. Ask it to plan a tiny starter install.
3. Approve one narrow project-local edit.
4. Verify the new behavior with simple prompts.

The recommended beginner starter bundle is:

- `rules/scoped-execution-lite.md`
- `rules/verification-lite.md`
- `rules/handoff-lite.md`

## Who This Helps

Use these recipes if:

- your agent keeps claiming work is complete before running proof commands
- your project instructions are scattered across chats, memory files, and vibes
- you want to install a friend's setup selectively instead of overwriting your own
- you want a repeatable way to extract public-safe docs from private workflows
- you want branch/release review prompts that check claims, security, and install paths

Skip this repo if you want a one-command harness installer. That is deliberately not the shape here.

## Repo Map

| Path | Purpose |
|---|---|
| `START_HERE.md` | Beginner first-run guide for model-first users. |
| `AGENTS.md` | Instructions for agents working on this repo itself. |
| `docs/transferability-roadmap.md` | Consolidation map for public assets, interview framing, beginner integration, and scanner ideas. |
| `install.md` | Audit-first, selective install guide. |
| `security.md` | Public-safety and local-harness safety checklist. |
| `prompts/` | Copy/paste prompts for auditing, installing, documenting, reviewing, and code archaeology. |
| `goal-recipes/` | Bounded `/goal`-style task briefs with done evidence and phase boundaries. |
| `rules/` | Small agent instruction fragments you can adapt into `AGENTS.md`, project rules, or memory. |
| `examples/` | Minimal examples for a project `AGENTS.md` and project brief. |

## Recommended Start

For beginners:

1. Read `START_HERE.md`.
2. Run the read-only audit prompt.
3. Install only the starter bundle if the plan looks safe.
4. Verify behavior with the checks in `START_HERE.md`.

For more experienced users:

1. Read `security.md`.
2. Copy `prompts/audit-current-agent-setup.md` into your agent and run it against your current setup.
3. Read the audit before copying anything from this repo.
4. Pick one rule or prompt to install manually.
5. Verify it changed behavior with the checks in `install.md`.

## Design Principles

- **Audit before install.** Inspect the target setup, compare gaps, recommend changes, then install only what the user chooses.
- **Markdown over machinery.** v1 should be reviewable by reading every file.
- **No private state.** Do not ship secrets, auth, logs, sessions, databases, private memory, or local machine paths.
- **Fresh evidence beats confidence.** Completion claims need a proof command, checklist, or observable artifact.
- **Scoped execution.** Agents should stay inside the requested files, phase, and repo unless explicitly invited out.
- **Portable patterns only.** These recipes describe behavior, not one person's private infrastructure.

## What Is Intentionally Excluded

- live MCP server configs
- cross-model commit hooks
- generated skills or workbench render/apply machinery
- Open Brain private memory or thought exports
- secrets templates beyond general safety guidance
- one-step installers
- global agent settings
- assumptions about any one user's home directory

## License

MIT. See `LICENSE`.
