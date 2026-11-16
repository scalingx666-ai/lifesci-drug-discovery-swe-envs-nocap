# Issue

**Title:** Fix preprocessing lincs

## Description

This PR accounts for the nested structure of `.h5ad` for dict. Therefore, all `'/'` in keys are replaced by `'|'` in the data. 
It also moves import in the seml executable for fast mongodb access.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb65b057c9a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.