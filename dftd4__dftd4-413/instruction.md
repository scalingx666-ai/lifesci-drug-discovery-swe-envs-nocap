# Issue

**Title:** Update dependencies and fix periodic test

## Description

Updates the dependencies and fixes the periodic tests, which changed due to the fix to the self-image indexing in Wigner-Seitz (grimme-lab/multicharge#71).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d900fc7a4748`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.