# Vision

`agent-harness-recipes` is a model-agnostic bootstrap layer for AI coding harnesses.

The goal is to take high-value operating patterns from real agent workflows and package them so another builder can audit their current setup, install the right subset, verify behavior, and keep improving the harness over time.

This repo starts as markdown because the first version must be readable, portable, and safe to adapt by hand. The long-term product is not "a folder of prompts." The product is a personalized operating layer that molds to the user's existing agent, project, and risk tolerance.

## Intent

Help builders turn AI coding tools into safer, more efficient working systems.

That means:

- capture proven scaffolding for agent work
- make it digestible for people who are new to agent setup
- keep installation audit-first and project-local by default
- translate patterns across Codex, Claude Code, Cursor, GitHub Copilot, Gemini, Aider, Cline, OpenHands, and generic `AGENTS.md`-style setups
- let users adopt only the parts that fit their current harness
- create an update path as the patterns improve

The one-time setup should feel like fitting a harness to the user's car, not bolting on someone else's cockpit.

## Why Now

AI coding agents are converging on the same basic capability set:

- read a repository
- create a plan
- edit files
- run commands
- use tools or MCP-style integrations
- work in the background
- open or review pull requests

The configuration surfaces are not converging as quickly. Each tool has different instruction files, rules, skills, memories, hooks, permissions, cloud environments, and review flows.

That creates a gap for users:

- providers ship capable agents
- open-source builders ship powerful wrappers
- beginners get access before they understand safe operating discipline
- experienced builders accumulate private harness patterns that are hard to transfer

This repo lives in that gap. It packages the operating discipline, not another agent runtime.

## Current Landscape Snapshot

As of May 2026, the important market pattern is convergence in capability and fragmentation in operating surface.

Provider tools:

- OpenAI Codex positions itself as an end-to-end coding agent with local, cloud, worktree, and parallel-agent workflows: <https://openai.com/codex/>
- Anthropic Claude Code exposes terminal workflows, MCP, skills, hooks, memory, scripting, and multi-agent work: <https://code.claude.com/docs/en/overview>
- GitHub Copilot cloud agent can research repositories, plan, edit, improve tests, update docs, resolve conflicts, and open pull requests: <https://docs.github.com/en/copilot/concepts/agents/cloud-agent/about-cloud-agent>
- Gemini Code Assist has IDE agent mode with planning, tool use, MCP extension, and approval flows: <https://docs.cloud.google.com/gemini/docs/codeassist/agent-mode>
- Cursor, Aider, Cline, OpenHands, and similar tools show that open-source and independent builders are moving just as quickly as platform providers.

Adoption and trust:

- Stack Overflow's 2025 AI survey shows high AI-tool usage, but lower trust and persistent frustration with AI output that is "almost right": <https://survey.stackoverflow.co/2025/ai>
- Beginners and model-first builders can now generate real software before they understand repo boundaries, test coverage, secrets, dependency risk, or rollback.

Implication:

- The scarce layer is not another model wrapper.
- The scarce layer is portable operating discipline: audit, scope, verification, handoff, adapters, and update checks.

## Who This Is For

Use this repo if you:

- build mostly by talking to a coding agent
- want better scope control, verification, and handoff behavior
- have scattered instructions across chats, docs, memory, and config
- want to borrow a friend's setup without overwriting your own
- want a model-agnostic way to improve Codex, Claude Code, Cursor, Copilot, Gemini, Aider, Cline, or another agent

The first user is a model-first beginner. The second user is an advanced builder who wants to package and transfer proven harness habits without leaking private state.

## What Success Looks Like

After using this repo, a user should have:

- a short audit of their current agent setup
- a recommended install plan classified as `NEW`, `UPGRADE`, `DUPLICATE`, `CONFLICT`, or `SKIP`
- one small project-local instruction change, if needed
- verification prompts that prove the behavior changed
- a rollback path
- a next-step path for goal briefs, release review, adapters, or future updates

The user's agent should become more predictable without becoming less inspectable.

## Product Shape

The repo should grow in layers:

1. **Canonical patterns**
   - Portable behaviors such as scoped execution, verification, handoff, goal briefs, release review, setup audit, and safe extraction.

2. **Prompt-first scanner**
   - A read-only setup audit that reports what exists, what is missing, what conflicts, and where a small project-local install should go.

3. **Harness adapters**
   - Tool-specific translation guidance for different instruction surfaces and agent workflows.

4. **Personalized bootstrap**
   - A guided install plan that adapts the canonical patterns to the user's current harness.

5. **Update path**
   - A way to compare a user's installed harness layer against newer repo patterns without blindly overwriting local choices.

Executable tooling may come later, but only after the markdown workflow proves the shape and safety boundaries.

## Non-Goals

This is not:

- another coding agent
- a one-command installer
- a global config overwrite
- a collection of private machine settings
- a bundle of live MCP configs, hooks, auth files, memory exports, or runtime state
- a promise that any model can be trusted without verification

The repo should make agent work more powerful by making it more legible.
