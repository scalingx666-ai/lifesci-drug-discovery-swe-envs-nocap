# Issue

**Title:** Duplicate compound compacting

## Description

1. Enforces one to one mapping between compounds and SMILES strings.
2. When dropping duplicates of compound ids or SMILES strings we also aggregate weight vectors.
3. Refactored and consolidated code that drops duplicate compounds into DatasetManager class.
4. Tests for features mentioned above.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0a898adf92f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.