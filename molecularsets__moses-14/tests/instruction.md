# Issue

**Title:** Precompute metrics on test splits

## Description

1. Added IntDiv2 metric
2. Metrics now have an intermediate state for precalculation
3. split_dataset script computes intermediate states for test and test_scaffolds splits
4. eval.py can use intermediate states to compute
5. added precalculation to run.py

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5312abf1f141`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.