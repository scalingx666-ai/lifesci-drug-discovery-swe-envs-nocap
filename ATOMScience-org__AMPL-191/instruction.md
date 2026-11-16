# Issue

**Title:** AD index computation changes for graphconv models and models with large training datasets

## Description

This branch fixes several issues with applicability domain index computations, plus some incidental bugs that I discovered while testing the changes:

- AD indices can now be computed for graphconv models, which were previously unsupported. In this case, the ADI uses the embedding vectors for each compound in place of feature vectors for the required distance computations.
- AD index computations for models with large training datasets are made feasible by using a random sample of the training compounds (1000 by default) instead of the entire dataset to estimate the distances of compounds from the training data.
- Comments have been cleaned up in the prediction functions to make the ADI-related parameters less cryptic.
- Loading model tarballs from the model_tracker/datastore was broken; it now works again.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `353228aafca2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.