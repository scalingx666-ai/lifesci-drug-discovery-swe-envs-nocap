# Issue

**Title:** Improve QRC

## Description

Currently the quick reaction coordinate (QRC) calculation performed to check a TS links reactants and products applies a constant magnitude displacement. This can lead to very small bond lengths for e.g. TSs involving hydrogen transfer. This PR adds a maximum displacement

- [x] Initial implementation
- [x] Fix `Distance` printed as `Distance(X.X Å)` in input files
- [x] Rebase 
- [x] Run & update benchmark

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `db4cb16102a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.