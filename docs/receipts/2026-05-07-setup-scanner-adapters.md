# Receipt: Setup Scanner And Initial Adapters

Date: 2026-05-07

## Goal

Add the first prompt-first scanner and manual adapter layer for the model-agnostic harness bootstrap direction.

## Phase Boundary

Completed in this slice:

- add a structured read-only setup scanner prompt
- add adapter index
- add initial adapters for generic `AGENTS.md`, Codex, Claude Code, and Cursor
- update README, install guide, architecture, and roadmap references

Not included in this slice:

- executable scanner
- one-command installer
- hooks
- MCP configs
- generated skills
- auth setup
- global trust settings
- runtime state
- GitHub Copilot, Gemini, Aider, Cline, or OpenHands adapters
- update-check prompt

## Changed Files

- `README.md`
- `install.md`
- `docs/architecture.md`
- `docs/transferability-roadmap.md`
- `prompts/setup-scanner.md`
- `adapters/README.md`
- `adapters/agents-md.md`
- `adapters/codex.md`
- `adapters/claude-code.md`
- `adapters/cursor.md`
- `docs/receipts/2026-05-07-setup-scanner-adapters.md`

## Decisions

- Scanner remains a prompt workflow, not a script.
- Adapters are manual translation docs, not install automation.
- First adapter targets are generic `AGENTS.md`, Codex, Claude Code, and Cursor because they cover the most immediate project-local instruction surfaces.
- Advanced surfaces such as hooks, MCP, memory, local skills, auth, and global config remain later phases requiring explicit approval.
- Future adapters should follow the same scan, classify, propose, approve, verify, remove shape.

## Verification

Run before final handoff:

- `git diff --check`
- referenced path existence check
- regex scan for private absolute paths and secret-like strings
- non-markdown artifact check
- executable-bit check

## Open Items

- Test `prompts/setup-scanner.md` against a disposable project.
- Test the beginner path with one trusted friend.
- Add adapter docs for GitHub Copilot, Gemini, Aider, Cline, and OpenHands after the adapter shape is proven.
- Add a prompt-first update checker for installed rules.
