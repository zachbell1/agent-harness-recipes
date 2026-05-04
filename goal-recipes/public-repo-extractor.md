# Goal Recipe: Public Repo Extractor

## Destination

Produce one small public-safe repo or artifact from private harness material.

## Source Context

Inspect only the sources needed for this artifact:

- existing public starter repos
- private source repos read-only
- planning notes
- project memory summaries
- local docs that describe behavior

Do not export raw private memory, logs, sessions, auth files, runtime state, databases, vendor imports, or local config.

## Invariants

- Start markdown-first unless the user explicitly approves code.
- No secrets, tokens, cookies, auth material, or private data.
- No one-step installer.
- No live MCP configs, hooks, trust settings, or global automation in v1.
- No personal absolute paths except placeholders or clearly labeled examples.
- Keep the repo small enough that a friend can review every file.

## Work Plan

1. Inventory candidate patterns.
2. Classify each pattern:
   - public-portable
   - public-template
   - friend-audit-prompt
   - private-local
   - secret-adjacent
   - vendor-system
   - too-complex-v1
3. Extract only public-portable, public-template, and friend-audit-prompt items.
4. Write README, install, and security docs.
5. Run a public-safety review.
6. Run a friend-install readiness review.

## Done Evidence

- final file tree
- source inventory summary
- classification summary
- public-safety checklist
- install/readiness checklist
- git status, if a repo was initialized
- open decisions before publishing

## Phase Boundary

Stop after the repo candidate and readiness audit. Do not publish, add hooks, add MCP configs, or refresh adjacent starter packs unless explicitly asked.
