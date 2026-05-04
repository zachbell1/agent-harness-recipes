# Goal Recipes

These are bounded task briefs for agent tools that support goal mode, long-running tasks, or structured work sessions.

Each recipe should define:

- **Destination:** the concrete artifact to produce
- **Source context:** what to inspect
- **Invariants:** what must not happen
- **Done evidence:** what proves completion
- **Phase boundary:** where to stop

Good goal recipes are not autonomy spells. They are containers for supervised work with a clear finish line.

## Recipes

| Recipe | Use when |
|---|---|
| `public-repo-extractor.md` | Turning private patterns into a public-safe starter repo. |
| `branch-release-critic.md` | Reviewing a branch or repo candidate before publishing. |
| `docs-from-reality.md` | Rebuilding docs from actual repo behavior. |

## Completion Discipline

A goal is complete only when the done evidence exists. A listening server, a plausible diff, or a confident summary is not enough.
