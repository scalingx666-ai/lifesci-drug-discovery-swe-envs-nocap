# Issue

**Title:** Fix the failure of chiral centre detection

## Description

- [x] Preserve initial molecule
- [x] Make the chiral centre detector to accept custom atom types
- [x] Pass the initial atom types to the chiral centre detector

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc987baf3bbe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.