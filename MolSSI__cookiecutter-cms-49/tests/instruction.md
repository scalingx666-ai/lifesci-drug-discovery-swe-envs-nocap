# Issue

**Title:** Updates Python and LGTM

## Description

- Bumps Python version numbers as Py 3.7 is now quite prolific and conda/conda-forge has finished their 3.7 migrations.
- Adds LGTM static code analysis.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e896e3fddc9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.