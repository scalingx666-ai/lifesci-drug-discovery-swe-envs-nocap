# Issue

**Title:** Bug compare models

## Description

- running predictions on classification models using the balancing weight transformers requires weights in the MinimalDataset representing the data to predict on

- using `get_multitask_perf_from_files_new` returned NaN metrics for single task models if they were mixed in with multitask models. Now, they both return the proper metrics.

((I am submitting this to be merged into bug_transformer_fitting but I can change it, I think it's independent I just need all of these bugs fixed in the same branch.))

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c5e23bc617d6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.