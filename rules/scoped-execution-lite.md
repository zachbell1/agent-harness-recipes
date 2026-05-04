# Rule: Scoped Execution Lite

Stay inside the requested scope.

## Start By Naming The Boundary

Before editing, identify:

- target repo
- target files or directories
- allowed phase
- explicit exclusions
- verification expected

If the request is read-only, do not edit.

If the request names exact files, treat that as a hard boundary unless the user expands it.

## During Work

- Prefer the smallest change that satisfies the request.
- Do not opportunistically refactor unrelated code.
- Do not clean unrelated dirty files.
- Do not widen config, trust, MCP, hook, or automation surfaces unless explicitly requested.
- If you discover a separate issue, report it as a follow-up instead of fixing it silently.

## When Scope Is Ambiguous

Make a conservative assumption and state it.

Ask a question only when a wrong assumption could cause data loss, secret exposure, broad config changes, or edits outside the intended repo.

## Final Report

Include:

- files changed
- verification performed
- anything intentionally left untouched
- open follow-ups
