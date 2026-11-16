# Issue

**Title:** Include all observations from the sciplex data

## Description

The first notebook simply does the gene matching with the lincs data, ignoring the subsetting from before. The second notebook is an updated version of the addition of SMILES strings to the `.obs`  dataframe. As a result all `.h5ad` files in the `PROJECT_DIR/'datasets'` folder are updated and ready to be used in our model sweeps.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `432f25e55f07`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.