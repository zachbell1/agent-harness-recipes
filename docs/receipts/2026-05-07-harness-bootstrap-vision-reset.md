# Receipt: Harness Bootstrap Vision Reset

Date: 2026-05-07

## Goal

Reframe `agent-harness-recipes` from a markdown prompt collection into a model-agnostic harness bootstrap layer while keeping the current phase docs-only and public-safe.

## Phase Boundary

Completed in this slice:

- define the updated intent
- add product vision
- add architecture and layer model
- update README positioning
- update roadmap with adapter, scanner, and update concepts

Not included in this slice:

- executable scanners
- one-command installers
- hooks
- MCP configs
- generated skills
- global agent settings
- runtime state
- repo rename or new repo creation

## Changed Files

- `README.md`
- `docs/vision.md`
- `docs/architecture.md`
- `docs/transferability-roadmap.md`
- `docs/receipts/2026-05-07-harness-bootstrap-vision-reset.md`

## Decisions

- Keep this work in the existing `agent-harness-recipes` repo.
- Treat current files as the v1 markdown bootstrap layer, not throwaway scaffolding.
- Position recipes as the distribution format, not the product.
- Define the long-term product as a personalized, model-agnostic operating layer for AI coding harnesses.
- Keep scanner and adapter work prompt-first and manual until the beginner path is tested.
- Future update workflows must compare and propose diffs instead of overwriting local customizations.

## Verification

Run before final handoff:

- `git diff --check`
- local file existence check for README-linked docs and top-level folders
- regex scan for private absolute paths and secret-like strings
- non-markdown artifact check
- executable-bit check

## Open Items

- Test the beginner path with one trusted friend.
- Add a dedicated prompt-first setup scanner.
- Add first adapter docs for generic `AGENTS.md`, Codex, Claude Code, and Cursor.
- Add an update-check prompt for installed rules.
- Decide later whether optional read-only tooling belongs in this repo after prompt workflows are proven.
