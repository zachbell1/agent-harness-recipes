# Prompt: Install With Gap Analysis

Use this after an audit. It asks the agent to compare this repo against the user's setup and install only selected items.

```text
I want to selectively install recipes from this markdown-only repo.

Before editing anything:

1. Read the setup audit from this session.
2. Read the recipe files I point you at.
3. For each recipe, classify it:
   - NEW: I do not have this behavior.
   - UPGRADE: I have a weaker version.
   - DUPLICATE: I already have equivalent behavior.
   - CONFLICT: It conflicts with existing instructions.
   - SKIP: It is not useful for my setup.
4. Recommend an ordered plan.
5. For every proposed edit, list:
   - target file
   - exact behavior change
   - backup needed
   - verification step
   - removal step

Rules:
- Do not install anything during the gap analysis.
- Do not overwrite whole config files.
- Do not edit secrets, auth files, runtime state, session logs, SQLite stores, MCP configs, hooks, or global trust settings.
- Prefer the smallest project-local change that creates the behavior.
- Ask me which numbered items to install.

After I choose items:
- Edit only the approved target files.
- Show the diff summary.
- Run or describe the agreed verification.
- Do not proceed to additional items without approval.
```
