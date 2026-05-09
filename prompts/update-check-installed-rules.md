# Prompt: Update Check Installed Rules

Use this after you have already installed one or more recipes from this repo and
want to compare your local instructions against newer recipe versions.

This is not an updater. It is a read-only comparison prompt. It should produce a
report first, then wait for approval before any edit.

```text
I previously installed or adapted rules from this markdown-only recipe repo.

Run an update check before changing anything.

Mode:
- Read-only.
- Do not edit, create, move, delete, install, migrate, or normalize anything.
- Do not produce a patch yet.

Goal:
- Identify which installed rules or prompts appear to come from this repo.
- Compare my installed text against the current recipe files I provide.
- Preserve local customizations by default.
- Recommend only small, approved updates.

Approved inspection scope:
- The current project or repo root.
- Project instruction files such as AGENTS.md, CLAUDE.md, .cursorrules,
  .cursor/rules, .github/copilot-instructions.md, README.md,
  docs/agent-notes.md, or equivalents.
- The exact installed rule files or prompt snippets I point you at.
- The current recipe files I provide from this repo.

Explicit non-targets:
- Secrets or .env files with real values.
- Auth stores, cookies, token stores, SSH keys, cloud credentials, or browser
  profiles.
- Session logs, chat transcripts, local memory databases, vector stores, or
  runtime traces.
- MCP server configs unless I explicitly approve reading a specific file.
- Git hooks unless I explicitly approve reading a specific file.
- Global trust settings, shell profiles, or agent auth directories.
- Generated runtime state, caches, build outputs, or unrelated personal files.

If a file might be sensitive, do not open it. Report its presence generically.

Report format:

1. Files Read
   - Exact files read.
   - One-line reason each file was relevant.

2. Installed Recipe Inventory
   Build a table with:
   - installed item
   - installed location
   - matching recipe file
   - confidence: high | medium | low
   - notes

3. Difference Classification
   For each installed item, compare the installed text against the current
   recipe and classify the difference:
   - SECURITY: closes a safety gap or prevents risky behavior.
   - CLARITY: makes the rule easier to understand without changing behavior.
   - BEHAVIOR: changes what the agent should do.
   - COMPATIBILITY: updates tool-specific wording or supported surfaces.
   - OPTIONAL: nice-to-have wording or examples.
   - LOCAL CUSTOMIZATION: intentionally different local behavior to preserve.
   - UNKNOWN: not enough evidence to classify safely.

4. Update Recommendation
   For each item, recommend:
   - APPLY: update is small, safe, and clearly improves the installed behavior.
   - REVIEW: user should inspect before deciding.
   - SKIP: no meaningful update needed.
   - PRESERVE LOCAL: keep the local customization.
   - BLOCKED: update cannot be judged without more context.

5. Proposed Update Plan
   - Ordered list of recommended updates.
   - Exact target files.
   - What behavior would change.
   - What local text should be preserved.
   - Backup needed.
   - Verification step.
   - Removal or rollback step.

6. Do Not Touch
   - Files, directories, or surfaces that should remain out of scope.
   - Include both detected sensitive surfaces and inferred boundaries.

7. Open Questions
   - Any missing context that affects the update decision.
   - Any user approval needed before reading more.

Rules:
- Distinguish confirmed facts from inferences.
- Cite exact files for every important claim.
- Prefer no update when the installed local behavior is already equivalent.
- Never overwrite local customizations silently.
- Do not recommend hooks, MCP configs, generated skills, auth setup, global
  settings, or automation as part of this update check.
- End with: "No edits made."

After I approve specific updates:
- Edit only the approved target files.
- Preserve unrelated local rules.
- Show the diff summary.
- Run or describe the agreed verification.
- Do not proceed to additional updates without approval.
```
