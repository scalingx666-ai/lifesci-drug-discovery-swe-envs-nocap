# Issue

**Title:** Multiclass class

## Description

I made small changes to `compare_models.get_filesystem_perf_results()` and `hyper_perf_plots` to allow for

1. more minimal examples to be used with the code
2. multiclass classification models to be used with the code

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `851ed02b1554`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.