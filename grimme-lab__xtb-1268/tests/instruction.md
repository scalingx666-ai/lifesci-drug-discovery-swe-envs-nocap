# Issue

**Title:** Avoid infinite `mopac` loops

## Description

- implemented some exits on fail checks
- we don't expect gradients for atoms
-

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `468c7209766e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.