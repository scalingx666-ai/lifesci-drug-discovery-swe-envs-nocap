# Issue

**Title:** Non metal allow

## Description

Refactor addressing several issues users were having:
1. Allowing non-metals to be "metal" centers.
2. More intuitive handling of "haptic" ligands.
3. Deeper explanation of n_symmetries vs. n_conformers added to documentation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2378ea4e4905`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.