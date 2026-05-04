# Prompt: Branch Release Critic

Use before merging, tagging, publishing, or sharing a repo candidate.

```text
Review this branch as a release critic. Prioritize defects, claim accuracy, security, and install-readiness over praise.

Inspect:
- git status
- branch and diff against the intended base
- README and install docs
- security-sensitive files
- generated or runtime-looking files
- tests or verification evidence

Check:
1. Does the repo contain only intended files?
2. Do README claims match actual contents?
3. Are there secrets, auth files, logs, sessions, databases, or private paths?
4. Is the install path audit-first and reversible?
5. Are exclusions documented clearly?
6. Are verification steps concrete?
7. Are there uncommitted or untracked files that should not ship?
8. Is the license/publishing status clear?

Output:
- Findings first, ordered by severity.
- If no findings, say "No findings".
- Then a release-readiness verdict: READY, READY_WITH_NOTES, or NOT_READY.
- Then exact open decisions before publishing.

Do not fix issues unless I explicitly ask.
```
