# Issue

**Title:** Pandas output

## Description

.

All scikit-mol transformer classes now support the scikit-learn `set_output` API. They can keep the data in DataFrames with meaningful column names.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ba3d1908f236`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.