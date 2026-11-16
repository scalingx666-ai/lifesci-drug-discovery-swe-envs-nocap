# Issue

**Title:** Catch ValueError: Sanitization error in compute_scaffold()

## Description

Catch `ValueError: Sanitization error: Explicit valence for atom greater than permitted` as invalid molecule, during call to `compute_scaffold()`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09e8a3154def`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.