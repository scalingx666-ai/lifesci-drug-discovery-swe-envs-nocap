# Issue

**Title:** Faster disentangle

## Description

Based on #38, which should be merged first.

I removed the crossvalidation and evaluate on just 10K of the test dataset by default. In my tests the disentanglement loss now takes ~1h to complete.

It probably wouldn't be too difficult to port the whole disentangling to GPU by using [Logistic Regressor from cuML](https://docs.rapids.ai/api/cuml/stable/api.html?highlight=logistic#cuml.LogisticRegression) instead of the sklearn Regressor (which runs on CPU).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `38905af8ec03`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.