# Issue

**Title:** Amanda shortlist

## Description

1. changed to two smallest datasets in the list
    - this means I had to change the smiles_col of MRP3_dataset to match the Delaney dataset, including in balancing_trans test which I re-ran and had no problems after changing
2. switched featurization to be first, then splitting
3. changed "already featurized" parameter in shortlist splitting code in hp search wrapper to True so it always looks for the featurized file - since featurizing now comes first, it finds it and doesn't re-calculate everything
5. didn't change number of models but they run pretty fast
6. Changed assert statement to verify that there are 18 models listed in the results df

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f8c44af59021`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.