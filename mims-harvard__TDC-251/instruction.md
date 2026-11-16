# Issue

**Title:** Integrate the CELLXGENE API with TDC DataLoader.get_data()

## Description

Given the name of any cellxgene dataset, provide a generator function yielding pandas dataframe chunks. benchmarking and get_splits() to follow.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3fcaa36bd083`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.