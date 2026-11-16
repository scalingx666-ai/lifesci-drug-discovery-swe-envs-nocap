# Issue

**Title:** [0.14.17] Loosen requirements with bounds

## Description

Loosens the requirements by establishing the current `==` as lower bounds (`>=`) and uses the next major version update as an upper bound (`<`).

Bumps patch version to `0.4.17` too.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b58df67f3a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.