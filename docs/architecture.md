# Architecture

This repo is organized around a simple pipeline:

```text
Proven pattern -> portable recipe -> setup audit -> harness-specific plan -> approved install -> verification -> update check
```

The current implementation is markdown-only. Future automation should preserve the same pipeline instead of bypassing it.

## Layers

### 1. Canonical Patterns

Canonical patterns are vendor-neutral behaviors that should survive model and tool changes.

Current examples:

- `rules/scoped-execution-lite.md`
- `rules/verification-lite.md`
- `rules/handoff-lite.md`
- `prompts/setup-scanner.md`
- `goal-recipes/README.md`
- `prompts/branch-release-critic.md`
- `prompts/codebase-archaeologist.md`
- `prompts/docs-from-reality.md`

Rules for this layer:

- describe behavior, not private infrastructure
- avoid tool-specific assumptions unless clearly labeled
- include verification and removal guidance when installation is involved
- stay small enough for a user to inspect

### 2. Scanner

The scanner is the discovery layer. In v1 it is a prompt workflow, not a script.

Its job is to inspect a user's current project and report:

- instruction files found
- current scope-control behavior
- current verification behavior
- current handoff behavior
- current safety boundaries
- duplicate or conflicting rules
- recommended starter actions
- exact target files for any proposed edit
- removal path
- verification prompts
- "do not touch" list

The scanner recommends. The user approves. Installation is a separate step.

### 3. Harness Adapters

Adapters translate canonical patterns into each user's actual agent surface.

Potential adapter targets:

- generic `AGENTS.md`
- Claude Code instructions, skills, hooks, and memory surfaces
- Codex project instructions and local skills
- Cursor rules
- GitHub Copilot repository instructions, custom agents, and cloud-agent workflows
- Gemini Code Assist and Gemini CLI instruction surfaces
- Aider conventions
- Cline and OpenHands workflows

Adapters should not copy the whole repo into a user's harness. They should point to the source pattern, explain the target file, and preserve the user's existing rules.

### 4. Bootstrap Plan

The bootstrap plan is the personalized install output.

It should classify each candidate pattern:

- `NEW`: behavior is missing
- `UPGRADE`: behavior exists but is weaker than the repo pattern
- `DUPLICATE`: equivalent behavior already exists
- `CONFLICT`: behavior conflicts with current setup
- `SKIP`: not useful for this harness

A good bootstrap plan includes:

- recommended first install
- target files
- exact diff or proposed section
- rollback path
- behavior verification
- parked items for later phases

### 5. Update Path

The update path lets users benefit as this repo improves.

The safe shape is a comparison workflow:

1. identify which patterns the user installed
2. compare installed text against current repo versions
3. classify changes as security, clarity, behavior, compatibility, or optional
4. propose a patch only for approved updates
5. preserve local customizations unless the user chooses otherwise

No future updater should silently overwrite user instructions.

## Current Repo Map

| Path | Layer | Role |
|---|---|---|
| `docs/vision.md` | Product frame | Explains intent, audience, and long-term direction. |
| `docs/architecture.md` | Product frame | Defines the layers and future expansion path. |
| `docs/receipts/` | Product frame | Durable decision receipts for substantial repo direction changes. |
| `START_HERE.md` | Bootstrap | Beginner first-run flow. |
| `install.md` | Bootstrap | Manual audit-first install and removal guide. |
| `rules/` | Canonical patterns | Small behavior primitives. |
| `prompts/` | Scanner and workflows | Copy/paste task prompts. |
| `adapters/` | Harness adapters | Manual translation docs for specific agent surfaces. |
| `goal-recipes/` | Canonical patterns | Structured long-running work briefs. |
| `examples/` | Bootstrap | Worked examples and starter files. |
| `security.md` | Safety | Public-safety and extraction checklist. |

## Version Boundaries

### V1: Markdown Bootstrap

V1 is the current phase.

Allowed:

- docs
- prompts
- rules
- examples
- goal recipes
- manual install and removal guidance

Forbidden:

- executable scanners
- one-command installers
- hooks
- live MCP configs
- auth setup
- global trust settings
- generated skill machinery
- runtime state
- private memory exports

### V2: Prompt Scanner And Adapters

V2 should add more structured prompt-first scanner output and tool-specific adapter docs.

Current examples:

- `prompts/setup-scanner.md`
- `adapters/agents-md.md`
- `adapters/claude-code.md`
- `adapters/codex.md`
- `adapters/cursor.md`

The adapter layer should remain manual and reviewable until the classification model is proven with real users. Additional adapters should follow the same shape before any script exists.

### V3: Optional Read-Only Tooling

Only after the prompt workflow has been dogfooded, a script may be useful.

Any script must:

- default to read-only
- require explicit file allowlists
- produce a report before edits
- keep install separate from scan
- avoid secrets, auth stores, session logs, private memory, hooks, MCP configs, and global settings by default

## Design Constraints

- Model-agnostic over provider-specific.
- Project-local before global.
- Diff review before behavior changes.
- Verification before completion claims.
- Manual and reversible before automated.
- Public-safe before comprehensive.
- Beginner-legible before harness-complete.
