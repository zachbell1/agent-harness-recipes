# Receipt: Context Check Gate

Date: 2026-05-07

## What Changed

- Added a canonical `Context Check Gate` section to `goal-recipes/README.md`.
- Added the gate to the goal brief builder prompt.
- Kept repo changes markdown-only and portable.

## What Was Not Touched

- No secrets, auth files, MCP allowlists, hooks, deploy config, trust settings, or vendor/system skill files were edited in this repo.
- No runtime processes were started or restarted.

## How To Use It

For goal-shaped work, Codex should run the gate before starting a new implementation slice or multi-step phase. The gate should estimate remaining context roughly, summarize repo/runtime/open-work state, and recommend one of `continue`, `checkpoint only`, `$outro now`, or `start fresh next turn`.

Skip the gate for tiny answers, one-command checks, and simple clarifications.
