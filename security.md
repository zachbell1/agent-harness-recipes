# Security And Public-Safety Checklist

These recipes are meant to be safe to share publicly. Keep them that way.

## Never Include

- secrets, tokens, API keys, cookies, bearer headers, refresh tokens, or service-role keys
- `.env` files with real values
- auth directories or credential stores
- SSH keys or cloud credentials
- session logs, transcripts, chat exports, or runtime traces
- SQLite databases or vector stores
- private memory excerpts or personal knowledge-base exports
- local-only absolute paths from a real machine unless clearly marked as placeholders
- vendor/system skill files copied as original work
- live MCP server configs
- global trust settings
- installer automation that edits a user's harness without an audit step

## Safe To Include

- original markdown rules
- copy/paste prompts
- placeholder examples such as `<PROJECT_DIR>` or `~/projects/example-app`
- checklists
- manual installation guidance
- warnings about secrets and runtime state
- public links to upstream docs, when useful

## Public Candidate Review

Before publishing a repo derived from private harness work, check:

| Check | Pass condition |
|---|---|
| Secrets | No real credentials or auth material. |
| Runtime state | No logs, sessions, databases, caches, generated traces, or local memory stores. |
| Paths | No personal absolute paths except labeled examples or placeholders. |
| Config blast radius | No trust widening, MCP allowlist expansion, hooks, or global configs in v1. |
| Source ownership | No vendor/system imports presented as original work. |
| Install behavior | No one-step overwrite installer. |
| Claims | README promises match what the repo actually contains. |
| Reviewability | A friend can read every file in one sitting. |

## Agent Safety Rules

When asking an agent to use these recipes:

- Require a target file list before edits.
- Require backups before changing existing files.
- Require a diff summary after edits.
- Require fresh verification before success claims.
- Stop at the requested phase boundary.
- Treat config, credentials, hooks, and automation as separate explicit phases.

## Sanitizing Private Patterns

When extracting a useful private harness pattern:

1. Describe the behavior in plain language.
2. Remove private names, project details, secrets, and local paths.
3. Convert machine-specific commands to placeholders.
4. Replace live automation with manual review steps.
5. Add a removal path.
6. Add a verification path.
7. Label anything still environment-specific.

If the result only works on one person's machine, keep it private.
