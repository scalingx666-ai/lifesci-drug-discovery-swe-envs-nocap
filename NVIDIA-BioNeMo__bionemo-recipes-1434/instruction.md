# Issue

**Title:** add fp8 to config

## Description

Add fp8 to esm2 15b config.
Also:
- reduce non-15b steps from 20k to 10k.
- remove an esm2 650m job
- remove esm2 3b from automated tracking

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8c4a616627e2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.