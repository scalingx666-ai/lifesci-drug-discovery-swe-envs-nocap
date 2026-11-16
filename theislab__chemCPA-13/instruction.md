# Issue

**Title:** Add logfold change evaluation

## Description

- Adds logfold computation to evaluation
- Fix evaluation via sampling size 
- Add additional `pert_category` in pp notebook

- close #3 (but plotting, eventually open separate issue for this)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e913ea7c1447`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.