# Issue

**Title:** Refactor dataframe conversion

## Description

Refactors dataframe-to-tensor conversion to improve reproducibility of downstream operations. Relevant for #484

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0ab5bc9585d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.