# Issue

**Title:** Aromatics, round 2

## Description

So far this PR enables the dekekulization of regions that show DIME.
Still TODO:

- [x] Implement `kekulize` function
- [x] Implement `dekekulize` function
- [x] Update README

Note that the (de)kekulize functions will remain separate from the `mark_aromatic_atoms`, because the latter is slightly more clever

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8be27ad99296`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.