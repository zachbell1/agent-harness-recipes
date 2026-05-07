# Example: Setup Scanner Report

This example shows what useful output from `prompts/setup-scanner.md` can look like.

The project is fictional. The file names are generic, and no secrets or private local paths are included.

## Starting Point

You have a project like this:

```text
example-app/
  README.md
  package.json
  AGENTS.md
  src/
```

You gave the agent these recipe files:

- `prompts/setup-scanner.md`
- `adapters/agents-md.md`
- `rules/scoped-execution-lite.md`
- `rules/verification-lite.md`
- `rules/handoff-lite.md`

You asked for a read-only scan.

## Expected Report

```text
## 1. Harness Surface

Detected tools:
- Generic repo-level agent instructions.

Instruction file types found:
- AGENTS.md
- README.md

Setup type:
- Project-local.

Inference:
- This project does not show evidence of a tool-specific rule surface such as CLAUDE.md, .cursorrules, or .cursor/rules.

## 2. Files Read

| File | Why it was read |
|---|---|
| AGENTS.md | Existing project-level agent instructions. |
| README.md | Project workflow and command hints. |
| package.json | Verification command discovery. |
| rules/scoped-execution-lite.md | Recipe comparison input. |
| rules/verification-lite.md | Recipe comparison input. |
| rules/handoff-lite.md | Recipe comparison input. |
| adapters/agents-md.md | Adapter guidance for repo-root AGENTS.md. |

## 3. Do Not Touch

- .env or .env.* files.
- Auth stores, cookies, token stores, SSH keys, or cloud credentials.
- Session logs, chat transcripts, memory databases, vector stores, or runtime traces.
- Git hooks.
- MCP configs.
- Global agent settings.
- Generated build output and caches.

No sensitive files were opened.

## 4. Current Behaviors

| Behavior | Current evidence | Strength | Notes |
|---|---|---|---|
| Scoped execution | AGENTS.md says to work in the repo, but does not mention named file or phase boundaries. | weak | Existing rule is directionally useful but broad. |
| Verification before completion claims | README lists `npm test`; AGENTS.md does not require evidence before saying done. | weak | Command exists, behavior rule is missing. |
| Handoff or session continuity | No handoff rule found. | absent | No current end-of-session format. |
| Read-only audit discipline | No explicit rule found. | absent | Agent may edit during setup unless prompted manually. |
| Security boundaries | AGENTS.md says not to edit secrets. | adequate | Could be stronger by naming auth, hooks, MCP, and global settings. |
| Rollback or removal path | No setup removal guidance found. | absent | Install plan should include removal. |
| Longer-goal planning | No goal brief or board rule found. | absent | Park for later. |
| Release or pre-publish review | No release critic rule found. | absent | Park for later. |

## 5. Recipe Comparison

| Recipe | Classification | Evidence |
|---|---|---|
| scoped-execution-lite.md | UPGRADE | AGENTS.md has a broad repo-scope rule, but not file, directory, phase, read-only, or explicit exclusion handling. |
| verification-lite.md | NEW | README has an `npm test` command, but no instruction requires fresh evidence before completion claims. |
| handoff-lite.md | NEW | No handoff behavior found in AGENTS.md or README.md. |
| adapters/agents-md.md | UPGRADE | Project already has AGENTS.md, so the adapter fits. Existing file should be preserved and updated, not replaced. |

## 6. Recommended Bootstrap

Smallest safe first install:
- Update the existing AGENTS.md with a short "Agent Operating Rules" section.

Target file:
- AGENTS.md

Behavior to add:
- Respect exact repo, file, and phase boundaries.
- Treat read-only tasks as read-only.
- Do not claim completion without fresh evidence.
- End substantial work with a concise handoff.

Why this first:
- The project already uses AGENTS.md, so no new instruction surface is needed.
- The change is project-local and easy to review.
- It adds the three starter behaviors without touching scripts, hooks, global settings, or tool-specific config.

Parked items:
- Goal brief workflow.
- Release critic prompt.
- Tool-specific adapters.
- Hooks, MCP configs, global settings, generated skills, and automation.

## 7. Proposed Verification

Boundary check:

```text
Boundary check: only inspect README.md and tell me what you would change. Do not edit.
```

Expected:
- The agent says the task is read-only.
- No files are edited.

Completion check:

```text
Completion check: are we done? Cite fresh evidence, or say what is not verified.
```

Expected:
- The agent cites a file check, diff check, test command, or explicit blocker.

Handoff check:

```text
Handoff check: end this session with current state, verification, open items, next action, and anything intentionally left untouched.
```

Expected:
- The agent produces a useful pickup note.

Project-specific command:

```text
npm test
```

Use only if the current task makes a behavior or code claim that tests should cover.

## 8. Removal Path

To remove:
- Delete the added "Agent Operating Rules" section from AGENTS.md.
- Start a fresh agent session.
- Ask the agent to summarize active project instructions.
- Confirm the removed scope, verification, and handoff rules no longer appear unless duplicated elsewhere.

## 9. Open Questions

- Should the first install include only the three starter rules, or also a pointer to the scanner prompt for future setup checks?
- Does this project use another agent tool outside this repo that has a separate rule surface?

No edits made.
```

## What Good Looks Like

The report is useful because it:

- names exact files read
- separates confirmed evidence from inference
- gives a "Do Not Touch" list
- classifies recipes before recommending changes
- proposes one small project-local target
- parks advanced surfaces
- includes behavior checks
- ends without editing

If a scanner report skips the files-read list, invents recipe contents, recommends global config first, or proposes hooks/MCP/automation as the first step, ask the agent to redo the scan.
