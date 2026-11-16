# Issue

**Title:** AD improvements

## Description

Fixed some +1 errors in AD calculation and created a test. Also calc_AD_kmean_dist now returns indexes for the nearest neighbors for each query. The function predict_from_model_file now has an option to append columns that lists the compound IDs of the nearest neighbors from the training set.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ce1a42687ba3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.