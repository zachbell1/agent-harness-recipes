# Receipt: Setup Scanner Dogfood

Date: 2026-05-07

## Goal

Run the new setup scanner prompt against a real project surface before adding more adapters or automation.

## Test Surface

Private local Python project with:

- repo-level agent instruction files
- project-specific constraints
- sensitive non-targets such as environment files, databases, caches, and generated review artifacts
- no public README discovered in the safe scan target set

The scan was read-only.

## Inputs Provided

- `prompts/setup-scanner.md`
- `adapters/agents-md.md`
- `rules/scoped-execution-lite.md`
- `rules/verification-lite.md`
- `rules/handoff-lite.md`

## Observed Result

The scanner shape was usable.

It could identify:

- existing project-level instruction files
- sensitive surfaces that should remain in the "Do Not Touch" list
- current project-specific security constraints
- missing or weak general operating behaviors around verification, handoff, read-only audit discipline, longer-goal planning, and release review
- an existing instruction file as the likely smallest project-local bootstrap target

## Follow-Up Decision

No immediate scanner prompt patch is required from this dogfood pass.

The next useful improvement is a worked example report, because users may understand the scanner faster if they can see a realistic output before running it.

## Open Items

- Add `examples/setup-scanner-report.md`.
- Test the scanner with one trusted friend.
- Add more adapters only after the scanner report format survives one external cold read.
