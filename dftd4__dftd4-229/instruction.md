# Issue

**Title:** Actinide Update

## Description

- add "refcn" (D3 CN) values for calculation of number of Gaussian weights
- update reference values in tests to include EEQ parameter update
- add `.EDISP` and `dftd4.txt` files to `.gitignore`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `edc2205abf6a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.