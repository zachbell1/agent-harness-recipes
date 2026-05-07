# Install Guide

This repo does not install itself. That is the point.

Use it as a small menu of prompts and rules. Ask your agent to audit your current setup first, then copy only the pieces you choose.

If you are new to agent setup, start with `START_HERE.md` before using the full install guide.

## What This Improves In The First Hour

- Agents stop making completion claims without fresh evidence.
- Project instructions become shorter and more explicit.
- Setup changes happen through reviewable diffs instead of overwrites.
- Branches get a security/readiness review before release.
- Long-running work leaves a handoff the next session can actually use.

## What Files It May Touch

Only the files you manually choose to create or edit. Common targets:

- a project-level `AGENTS.md`
- a project brief such as `docs/project-brief.md`
- agent rule files in your tool's supported rules directory
- saved prompt snippets in your notes

This repo does not require changes to:

- shell profiles
- credential files
- MCP server configs
- git hooks
- global trust settings
- agent auth directories
- session logs or memory databases

## Back Up First

Before editing an existing setup, ask your agent to list the target files and make backups of only the files it will touch.

Example backup wording:

```text
Before changing anything, list every file you plan to edit. For each existing file, create a timestamped backup next to it. Do not edit files outside that list.
```

## Selective Install Path

1. Run `prompts/setup-scanner.md`.
2. Read the scanner report and confirm the "Do Not Touch" list.
3. Pick the matching adapter in `adapters/`, if one exists.
4. Run `prompts/install-with-gap-analysis.md` against the scanner report, selected adapter, and selected recipe files.
5. Choose one item from the plan.
6. Copy that item manually or ask the agent to make the narrow edit.
7. Review the diff.
8. Run the verification check for that item.

Recommended first install:

- Add the starter bundle to your project instructions or `AGENTS.md`:
  - `rules/scoped-execution-lite.md`
  - `rules/verification-lite.md`
  - `rules/handoff-lite.md`
- Ask the agent to make one small change in a disposable branch.
- Confirm it reports the exact command or checklist used before claiming completion.

Default target:

- If your project has no agent instruction file, create a repo-root `AGENTS.md`.
- If your project already has an instruction file, append the smallest clear section instead of replacing it.
- Keep the install project-local until you have proven the rules help.

Optional local goal adapter:

- Keep this repo as the source of truth.
- Add a short global or project instruction that says long-running goals should use your chosen clone path, such as `<AGENT_HARNESS_RECIPES_DIR>/goal-recipes/README.md`.
- If your agent supports local skills, create a thin `goal` skill that points back to these files instead of copying the full framework.
- The adapter should trigger on `/goal`, "goal skill", long-running tasks, multi-step implementation, audit/docs/release-critic passes, and source-pipeline first slices.
- Do not install external goal automation until you have dogfooded the markdown workflow and identified concrete friction.

## Adapter Path

Use adapters when the scanner identifies a specific harness surface.

Current adapter docs:

- `adapters/agents-md.md`
- `adapters/codex.md`
- `adapters/claude-code.md`
- `adapters/cursor.md`

Adapters are manual translation guides. They do not install anything by themselves.

Do not use multiple adapters at once for a first install. Pick the surface the project already uses, or use `AGENTS.md` when the user wants a portable project-local target.

## Verify It Worked

Use the checklist that matches what you installed:

| Installed item | Verification |
|---|---|
| `verification-lite.md` | Ask "are we done?" after a code/doc change. The agent should cite fresh evidence or say the claim is unverified. |
| `scoped-execution-lite.md` | Give a task with explicit file boundaries. The agent should restate the boundary and avoid unrelated edits. |
| `handoff-lite.md` | End a session. The agent should produce current state, changed files, verification, open items, and next action. |
| `examples/AGENTS.md` | Ask the agent to explain the project operating rules. It should summarize the local file, not generic preferences. |
| `branch-release-critic` prompt | Run it before publishing. It should inspect diff, docs, security, install path, and claim accuracy. |

## Remove It

Removal is manual and should be boring:

1. List the files you copied or edited.
2. Remove copied prompt/rule files you no longer want.
3. Restore backups for edited files, or revert the specific diff hunks.
4. Start a fresh agent session and ask it to summarize current instructions.
5. Confirm the removed rule no longer appears in the summary.

## Audit-First Install Prompt

Use this if you want an agent to help install selectively:

```text
I have a markdown-only agent-harness recipe repo. Before installing anything:

1. Run a read-only setup scan using the scanner prompt I provide.
2. Inspect the recipe and adapter files I point you at.
3. Classify each recipe or adapter as NEW, UPGRADE, DUPLICATE, CONFLICT, or SKIP.
4. Recommend a prioritized plan.
5. Ask me which exact items to install.

Do not install anything during the audit. Do not overwrite existing files. Do not edit secrets, auth files, hooks, MCP configs, session logs, SQLite stores, or private memory.
```

## What Is Intentionally Excluded

- no executable scripts
- no hooks
- no MCP configs
- no auth setup
- no global installer
- no generated skill machinery
- no private memory export
- no assumptions about a specific agent vendor
