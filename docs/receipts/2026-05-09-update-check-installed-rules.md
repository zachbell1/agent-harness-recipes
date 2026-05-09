# Receipt: Update Check Installed Rules

Date: 2026-05-09

## What Changed

- Added `prompts/update-check-installed-rules.md`.
- Added a mandatory timestamped backup requirement before editing existing
  target files during approved updates.
- Updated `docs/architecture.md` so the update path points to the new
  prompt-first checker.
- Updated `docs/transferability-roadmap.md` so the prompt is listed as a public
  asset and the future slice is now dogfooding the prompt.
- Updated `README.md` so the prompt directory advertises update checks and the
  recommended path mentions read-only comparison before updating.

## Why

The Agent/Harness OS boundary review said public `agent-harness-recipes` should
expand through portable docs, prompts, and examples before any scripts, hooks,
MCP configs, or live automation. This prompt gives users a safe way to compare
installed rules against newer recipe versions while preserving local
customizations by default.

## What Was Not Touched

- No scripts were added.
- No hooks, MCP configs, auth setup, global trust settings, generated skill
  machinery, runtime state, private memory, logs, sessions, databases, or live
  harness config were added or changed.
- No private harness source/apply machinery, local workflow registry details,
  runtime config, memory-system internals, or knowledge-system internals were
  copied into the public repo.

## Verification

- Run `git diff --check`.
- Review the new prompt against `security.md` public-safety rules.
- Confirm the repo remains markdown-only for this slice.

## Next

Dogfood `prompts/update-check-installed-rules.md` against one installed starter
bundle or run the cold-read/friend-install audit before adding advanced workflow
packs.
