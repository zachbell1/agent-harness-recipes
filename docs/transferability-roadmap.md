# Transferability Roadmap

This roadmap tracks the path from the current markdown recipes to a model-agnostic harness bootstrap layer.

The goal is to make useful agent habits portable and installable without copying private machines, secrets, auth state, logs, local memory, hooks, MCP configs, or global trust settings.

For the product frame, read `docs/vision.md`.

For the layer model, read `docs/architecture.md`.

## Core Thesis

AI-assisted coding becomes more reliable when the agent has a small operating layer:

- it audits the current setup before changing anything
- it stays inside the requested repo, files, and phase
- it proves work before saying it is done
- it leaves a handoff the next session can trust
- it uses goal briefs for longer work instead of drifting across tasks

This repo is the first public slice of that operating layer. The long-term shape is a personalized bootstrap: inspect the user's current harness, classify gaps, install only approved pieces, verify behavior, and later compare for safe updates.

## Public Assets In This Repo

| Asset | What it transfers | Beginner value |
|---|---|---|
| `docs/vision.md` | Product intent and long-term direction. | Explains why this exists before users copy rules. |
| `docs/architecture.md` | Layer model for patterns, scanner, adapters, bootstrap, and updates. | Shows what is v1 now and what should wait. |
| `START_HERE.md` | A first-run path for model-first users. | Gives exact prompts for audit, install plan, approval, and behavior checks. |
| `examples/beginner-first-install.md` | A worked install example. | Shows what useful model output should look like. |
| `examples/setup-scanner-report.md` | A worked scanner report example. | Shows what useful scanner output should include before any install plan. |
| `rules/scoped-execution-lite.md` | Scope boundary discipline. | Reduces unrelated edits and config drift. |
| `rules/verification-lite.md` | Evidence-backed completion claims. | Stops "looks good" from replacing tests, checks, or explicit blockers. |
| `rules/handoff-lite.md` | End-of-session continuity. | Makes future sessions easier to resume. |
| `prompts/audit-current-agent-setup.md` | Read-only setup discovery. | Helps users understand their current agent rules before installing anything. |
| `prompts/setup-scanner.md` | Structured scanner report. | Produces a safer harness bootstrap report before install planning. |
| `prompts/install-with-gap-analysis.md` | Selective install planning. | Classifies recipes before edits and asks for approval. |
| `prompts/codebase-archaeologist.md` | Read-only repo orientation. | Helps an agent map unfamiliar code before editing. |
| `prompts/docs-from-reality.md` | Documentation grounded in observable behavior. | Avoids aspirational or stale README claims. |
| `prompts/branch-release-critic.md` | Release-readiness review. | Checks claim accuracy, security, file tree, and install path before sharing. |
| `adapters/` | Harness-specific translation docs. | Shows where portable patterns fit for common tools. |
| `goal-recipes/README.md` | Goal Brief + Board + Receipt framework. | Gives longer work a phase boundary, robustness probes, done evidence, and completion audit. |

## Adjacent Patterns To Consolidate Later

These are related public or public-candidate directions, but they should not be copied into this repo wholesale:

- persistent-memory starter guidance
- audit-first friend setup guides
- cross-model review starter guidance
- portable skill/adapter patterns
- scanner-style setup evaluation
- update-check workflows for installed harness rules
- interview/demo walkthroughs

Each should pass through the same extraction filter before publication:

1. describe the portable behavior
2. remove private state, secrets, local paths, logs, sessions, and runtime data
3. replace live automation with audit-first manual steps
4. add install, verify, and remove paths
5. keep the result small enough for a friend to review
6. define how future updates would be compared without overwriting local choices

## Interview And Portfolio Story

Use this project as a concrete systems story:

### Problem

AI coding assistants are powerful but often fail in predictable ways:

- they overclaim completion
- they edit outside the intended scope
- they lose project context between sessions
- they make setup changes without a rollback path
- beginners do not know which agent rules to install or trust
- different tools expose similar agent power through different config surfaces

### Approach

Build a portable operating layer around the model:

- read-only audit before install
- project-local instructions before global config
- narrow starter rules before advanced automation
- explicit verification before completion claims
- handoff notes before context is lost
- goal briefs for longer or riskier work
- adapter guidance for each harness surface after the canonical patterns are clear
- update checks that compare and recommend rather than overwrite

### Proof Points

This repo can demonstrate:

- a beginner opening `START_HERE.md`
- an agent auditing a fresh project without edits
- an install plan that classifies starter rules as new, duplicate, upgrade, conflict, or skip
- one approved project-local instruction file change
- behavior checks proving scope, verification, and handoff rules are active
- release-review prompts that inspect claims before public sharing
- a clear architecture for future scanners and harness adapters

### Demo Script

1. Open a small disposable project.
2. Run the read-only audit prompt from `START_HERE.md`.
3. Ask for the starter bundle plan.
4. Approve one project-local `AGENTS.md` edit.
5. Run the boundary, completion, and handoff checks.
6. Show the before/after difference in agent behavior.

The demo should not require secrets, global settings, MCP servers, hooks, paid APIs, private memory, or production credentials.

## Beginner Integration Funnel

The beginner path should stay simple:

1. **Orient:** read `START_HERE.md`.
2. **Audit:** ask the agent to inspect project-local instructions read-only.
3. **Compare:** classify the starter bundle against existing behavior.
4. **Approve:** install only selected items into one project-local file.
5. **Verify:** run behavior checks.
6. **Extend:** add advanced prompts or goal recipes only after the starter bundle works.

The first success condition is modest: one project gets better scope control, completion evidence, and handoff behavior.

## Harness Adapter Path

Adapters should translate canonical patterns into each user's actual tool surface.

Initial adapter candidates:

- generic `AGENTS.md` (`adapters/agents-md.md`)
- Codex project instructions and local skill pointers (`adapters/codex.md`)
- Claude Code instructions, skills, hooks, and memory boundaries (`adapters/claude-code.md`)
- Cursor rules (`adapters/cursor.md`)
- GitHub Copilot repository instructions, custom agents, and cloud-agent workflows
- Gemini Code Assist or Gemini CLI instruction surfaces
- Aider conventions
- Cline and OpenHands workflows

Adapter docs should:

- start from a setup audit
- name the exact target files
- preserve existing user rules
- avoid copying private machine state
- install one narrow behavior at a time
- include verification and removal paths

The first adapters are manual docs only. They do not change the v1 boundary because they do not add executable tooling or live config.

## Scanner Concept

A scanner would be useful, but it should start as a prompt workflow before becoming a script.

### Default Mode

Read-only. No edits.

### Inputs

- project path or repo root
- agent tool in use, such as Cursor, Claude Code, Codex CLI, or another coding assistant
- approved instruction files or config files to inspect
- whether the user wants project-local recommendations only
- whether global config, hooks, MCP configs, auth, logs, or memory are explicitly off limits

### Safe Inspection Targets

- repo-root instruction files such as `AGENTS.md`, `CLAUDE.md`, `.cursorrules`, or equivalents
- README and docs that describe workflow
- project-local rule files
- package metadata only when needed to identify verification commands

### Explicit Non-Targets

- secrets and `.env` files with real values
- auth stores, cookies, token stores, or SSH keys
- session logs and chat transcripts
- local memory databases or vector stores
- MCP server configs
- git hooks
- global trust settings
- shell profiles
- generated runtime state

### Output Report

The scanner should produce:

- instruction files found
- current scope-control behavior
- current completion-verification behavior
- current handoff behavior
- current security boundaries
- duplicate or conflicting rules
- recommended starter bundle actions
- exact target files for any proposed edit
- removal path
- verification prompts
- "do not touch" list

### Recommendation Classes

- `NEW`: behavior is missing
- `UPGRADE`: behavior exists but is weaker than the starter rule
- `DUPLICATE`: equivalent behavior already exists
- `CONFLICT`: starter rule conflicts with existing instructions
- `SKIP`: not useful for this setup

### Guardrail

The scanner recommends. The user approves. Installation remains a separate step.

## Update Concept

Once people install these patterns, they need a safe way to receive improvements.

The update workflow should:

1. identify which repo patterns are already installed
2. compare installed text against the current repo pattern
3. classify differences as security, clarity, behavior, compatibility, or optional
4. preserve local customizations by default
5. propose exact diffs for approved updates only

No updater should silently rewrite a user's harness.

## Future Build Slices

1. Test the beginner path with one trusted friend.
2. Test `prompts/setup-scanner.md` with one trusted friend.
3. Add examples for GitHub Copilot, Gemini, Aider, Cline, and OpenHands after the adapter format is proven.
4. Add an interview/demo walkthrough with before/after transcripts.
5. Add a friend-audit checklist for reviewers trying this repo cold.
6. Add a prompt-first update checker for installed rules.
7. Decide whether the scanner remains prompt-only or becomes an optional read-only script.
8. If a script is added later, keep it read-only by default and require explicit file allowlists.

## Not In Scope Yet

- one-command installers
- automatic edits to global agent settings
- hooks
- MCP configs
- auth setup
- credential templates with real values
- private memory exports
- generated skill machinery
- runtime state import/export
- silent update automation

## Current Readiness

The repo is ready for a cold-read beginner audit when a reviewer can:

- find `START_HERE.md` from the README
- understand the starter bundle without knowing harness terminology
- run the audit prompt without exposing secrets
- get a concrete install plan before edits
- verify changed behavior after one project-local install

If that reviewer gets confused before the first behavior check, the next improvement should happen in `START_HERE.md` or `examples/beginner-first-install.md`, not in automation.
