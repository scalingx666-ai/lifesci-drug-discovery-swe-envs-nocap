# Issue

**Title:** Clean up settings

## Description

Applies two minor changes:
* Bumps `attrs` to latest release. Solves the original problem for the  `alias` workaround, but upgrading surfaced another issue, hence keeping the workaround.
* Moves the factory function to the global scope (which I noticed is possible while working on the first point) to improve readability

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9944e61dbc84`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.