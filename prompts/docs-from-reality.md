# Prompt: Docs From Reality

Use when a repo works but the docs are vague, aspirational, or stale.

```text
Rewrite or audit the docs from observable repo reality.

Rules:
- Inspect the actual file tree, configs, entry points, commands, and tests.
- Do not invent features.
- Do not describe planned behavior as current behavior.
- Mark anything unverified as unverified.
- Keep install and verification steps runnable by a new user.

Build the docs around:
1. What this repo does today.
2. Who it is for.
3. What files matter.
4. How to install or use it selectively.
5. How to verify it worked.
6. How to remove it.
7. What is intentionally excluded.
8. Known limitations and open decisions.

Before claiming the docs are complete:
- Compare each major README claim against a file, command, or checklist.
- List any claims you could not verify.
- Confirm no private paths, secrets, runtime state, or local-only assumptions were added.
```
