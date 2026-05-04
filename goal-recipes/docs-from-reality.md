# Goal Recipe: Docs From Reality

## Destination

Produce docs that accurately describe what the repo does now.

## Source Context

Inspect:

- file tree
- entry points
- package/build metadata
- tests
- config templates
- existing README/docs
- recent git history, if useful

## Invariants

- No aspirational claims.
- No unverified setup steps.
- No hidden dependencies.
- No private paths or local-only assumptions.
- No generated runtime state in docs examples.

## Work Plan

1. Map the repo's actual behavior.
2. Identify docs that are missing, stale, or misleading.
3. Rewrite docs around observable facts.
4. Add install, verify, remove, and excluded sections.
5. Check every major claim against the repo.

## Done Evidence

- updated docs
- claim-to-evidence checklist
- commands or manual checks used for verification
- unresolved claims explicitly labeled
- security/public-safety scan if the docs are public-facing

## Phase Boundary

Stop after docs and verification notes. Do not change behavior while doing a docs-from-reality pass unless explicitly asked.
