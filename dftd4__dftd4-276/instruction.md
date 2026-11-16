# Issue

**Title:** Add wB97X-D4 parameters

## Description

- rename `wb97x` to `wb97x-2008`
- add Goerigk's D4 parameters for wB97X-D4 (as `wb97x`, consistent with B97M and wB97M)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `05e6eb0208dc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.