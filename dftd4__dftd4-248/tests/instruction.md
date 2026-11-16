# Issue

**Title:** Fix passing atomic numbers from PySCF to D4 interface

## Description

- use atomic symbols and [pyscf's charge function](https://github.com/pyscf/pyscf/blob/bf0b1db22556a3c1b4c34426ea8627e636c1b096/pyscf/data/elements.py#L1136) for obtaining atomic numbers

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3a1c21ec655d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.