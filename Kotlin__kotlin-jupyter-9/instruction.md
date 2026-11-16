# Issue

**Title:** Create installation directory if it does not exist

## Description

Installation of the kernel fails if the kernel install directory does not exist. This fix ensures that the missing directories are created so the installation succeeds in this scenario.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `586e1a06f505`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.