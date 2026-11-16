# Issue

**Title:** Add API for molecular optimization baseline.

## Description

Adds:
- `dockstring.benchmarks` module to hold benchmark-related code.
- Implementations of 3 benchmark objectives from original paper
- Testing of the above implementations.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c123d7a602dd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.