# Prompt: Setup Scanner

Use this when you want a structured, read-only report of an AI coding harness before installing anything from this repo.

This is not an installer. It is the scanner layer in prompt form.

```text
Scan my current AI coding setup and produce a structured harness bootstrap report.

Mode:
- Read-only.
- Do not edit, create, move, delete, install, migrate, or normalize anything.
- Do not produce a patch yet.

Goal:
- Identify how my current project tells AI coding agents what to do.
- Compare the current setup against the portable patterns in the recipe files I provide.
- Recommend a small, reversible bootstrap plan that fits my current harness.

Approved inspection scope:
- The current project or repo root.
- Project instruction files such as AGENTS.md, CLAUDE.md, .cursorrules, .cursor/rules, .github/copilot-instructions.md, README.md, docs/agent-notes.md, or equivalents.
- Project-local docs that describe build, test, verification, release, or agent workflow.
- Package metadata only when needed to identify verification commands.
- The recipe files I explicitly point you at.

Explicit non-targets:
- Secrets or .env files with real values.
- Auth stores, cookies, token stores, SSH keys, cloud credentials, or browser profiles.
- Session logs, chat transcripts, local memory databases, vector stores, or runtime traces.
- MCP server configs unless I explicitly approve reading a specific file.
- Git hooks unless I explicitly approve reading a specific file.
- Global trust settings, shell profiles, or agent auth directories.
- Generated runtime state, caches, build outputs, or unrelated personal files.

If a file might be sensitive, do not open it. Report its presence generically.

Report format:

1. Harness Surface
   - Agent tool or tools detected, if any.
   - Instruction file types found.
   - Whether the setup appears project-local, global, mixed, or unknown.

2. Files Read
   - Exact files read.
   - One-line reason each file was relevant.

3. Do Not Touch
   - Files, directories, or surfaces that should remain out of scope.
   - Include both detected sensitive surfaces and inferred boundaries.

4. Current Behaviors
   Build a table with:
   - behavior
   - current evidence
   - strength: absent | weak | adequate | strong | unknown
   - notes

   Check at least:
   - scoped execution
   - verification before completion claims
   - handoff or session-continuity behavior
   - read-only audit discipline
   - security boundaries
   - rollback or removal path
   - longer-goal planning
   - release or pre-publish review

5. Recipe Comparison
   For each recipe or adapter file I provide, classify it as:
   - NEW: behavior is missing
   - UPGRADE: behavior exists but is weaker
   - DUPLICATE: equivalent behavior already exists
   - CONFLICT: it conflicts with existing instructions
   - SKIP: not useful for this setup

   Include evidence for each classification.

6. Recommended Bootstrap
   - Smallest safe first install.
   - Exact target file or files.
   - Exact behavior to add.
   - Why this is the first step.
   - What to leave parked.

7. Proposed Verification
   - Boundary check prompt.
   - Completion check prompt.
   - Handoff check prompt.
   - Any project-specific test or build command, if safely discoverable.

8. Removal Path
   - How to undo the proposed install.
   - Which files would need restoration or hunk removal.

9. Open Questions
   - Any missing context that affects the install plan.
   - Any user approval needed before reading more.

Rules:
- Distinguish confirmed facts from inferences.
- Cite exact files for every important claim.
- Do not recommend global settings until a project-local path has been considered.
- Do not recommend hooks, MCP configs, generated skills, auth setup, or automation as the first install.
- End with: "No edits made."
```
