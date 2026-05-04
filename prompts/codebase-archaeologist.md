# Prompt: Codebase Archaeologist

Use when entering an unfamiliar repo and needing a grounded map before edits.

```text
Act as a codebase archaeologist. Start read-only.

Goal:
Understand what this repo is, how it works, what is safe to change, and where the next useful edit belongs.

Inspect:
- file tree
- README/docs
- package or build metadata
- tests
- entry points
- recent git history
- project-level agent instructions

Report:
1. What the repo appears to do.
2. Main modules and ownership boundaries.
3. How to run or verify it.
4. Current dirty state.
5. Risky areas to avoid.
6. Any stale or misleading docs.
7. Suggested first safe edit, if relevant.

Rules:
- Do not edit files in the archaeology pass.
- Separate observed evidence from inference.
- Prefer exact file references over broad summaries.
- If the repo has private or secret-looking files, do not open them; report their presence generically.
```
