# Issue

**Title:** Fix and speed up evaluation

## Description

- fix nan issues in `evaluate_r2`
- change solver for logistic regression in `evaluate_disentanglement`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `33ea48a663e7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.