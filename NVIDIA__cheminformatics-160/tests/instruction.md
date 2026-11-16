# Issue

**Title:** Fix regressions in metric plotting

## Description

This PR accomplishes the following: 

- Fixes a regression in the data loading important for plotting involving fingerprint files
- Plotting is configurable in yaml file -- can be moved a different configuration file later
- Updates to plotting code to allow datasets from different directories (eg different models) to be loaded
- Updates to plotting code to accommodate changes in labels / naming

@rilango  mentioned that he has ideas for improving the data storage. This code can be updated and changed later, what I'd like to do now is get this code incorporated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8977e36b2164`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.