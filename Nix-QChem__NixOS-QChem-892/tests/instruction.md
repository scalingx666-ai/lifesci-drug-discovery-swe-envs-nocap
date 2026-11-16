# Issue

**Title:** sharc: 4.0.2 -> 4.1

## Description

Updates the Sharc MD code to its latest version. Requires some small patches to Fortran code. https://github.com/sharc-md/sharc4/releases/tag/v4.1

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `805540e50933`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.