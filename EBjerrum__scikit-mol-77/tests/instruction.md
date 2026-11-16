# Issue

**Title:** Jaccard fix

## Description

Changing the check_params of the base AD estimator to avoid future warnings. 

Casting as boolean if distance metric jaccard or tanimoto is selected in kNN AD estimator avoids dataconversion warnings from sci-py.  

Fixing notebook 13 which failed on the standard subset dataset included with the code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fe0e97d42e2b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.