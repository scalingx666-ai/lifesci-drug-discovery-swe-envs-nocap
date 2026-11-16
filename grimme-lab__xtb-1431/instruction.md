# Issue

**Title:** Validate MD restart files

## Description

, which tried to restart an MD calculation without a restart file being present. This just tightens up the reporting, so that it informs the user a restart couldn't be found, rather than producing a traceback when trying to read a non-existent file.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b31754bf3c7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.