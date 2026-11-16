# Issue

**Title:** Optimization of D3 calculation

## Description

- move redundant calculations out of inner loops
- additional caching in ASE calculator to avoid object reconstruction
- match default in Python API with CLI to require opt-in for ATM

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `87efc010cd74`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.