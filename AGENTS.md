# Agent Instructions

Use these instructions when working in this repository.

## Scope

- Stay inside this repository unless the user explicitly asks otherwise.
- Keep v1 markdown-first: prompts, recipes, rules, examples, and docs.
- Do not add scripts, hooks, MCP configs, installers, generated skill machinery, or live automation unless explicitly requested.
- Do not copy private memory, logs, sessions, auth material, local databases, vendor/system skills, or machine-specific config into this repo.

## Editing Style

- Prefer small, reviewable doc changes.
- Preserve the audit-first install philosophy: inspect, compare, recommend, then let the user choose.
- Keep examples generic and portable. Use placeholders such as `<PROJECT_DIR>` rather than personal absolute paths.
- If a change makes the repo less safe to share publicly, call that out before editing.

## Verification

For doc-only changes, verify by checking:

- `git diff --check`
- the changed docs for internal consistency
- `security.md` public-safety rules when adding examples, configs, or install guidance

Before claiming publish readiness, also check:

- no secrets, private paths, runtime state, or local-only config were added
- README claims match the actual file tree
- install guidance remains manual, selective, and reversible
- license status is clear

## Handoff

End substantial changes with:

- changed files
- verification performed
- open publishing decisions
- anything intentionally left out of scope
