# Issue

**Title:** Add parallel processing to MoleculeCSVDataset using joblib

## Description

*Issue #, if available:* #64 

*Description of changes:*
Add new arg n_jobs to MoleculeCSVDataset initialization defaulting to 1. If this is > 1, joblib is used to parallelize _pre_process.

By submitting this pull request, I confirm that you can use, modify, copy, and redistribute this contribution, under the terms of your choice.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a28f6db891e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.