# Prompt: Audit Current Agent Setup

Use this before installing recipes from someone else's harness.

```text
Audit my current AI coding setup. Do not change anything.

Scope:
- Inspect project-level agent instructions such as AGENTS.md, CLAUDE.md, .cursorrules, docs/agent-notes.md, or equivalent files if present.
- Inspect only explicitly relevant global agent config paths that I approve.
- Do not read secrets, auth files, session logs, private memory databases, cookies, token stores, or unrelated personal files.

Report:
1. Current instruction files found.
2. Current rules or preferences that affect coding behavior.
3. Current hooks, MCP/tool configs, or automation surfaces, if I approved reading them.
4. Current verification expectations.
5. Current handoff/session-continuity expectations.
6. Current security boundaries.
7. Risks or conflicts you see.

Output:
- A table titled "Current Setup".
- A table titled "Potential Gaps".
- A short "Do Not Touch" list.
- No installation plan yet unless I ask for one.

Important:
- Read files before summarizing them.
- Distinguish confirmed facts from guesses.
- If you cannot inspect something safely, say so explicitly.
```
