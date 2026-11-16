# Issue

**Title:** WIP: GPU accelerated Spearman R

## Description

This is a MR for the GPU accelerated version of Spearman R, however as can be seen in the notebook [here](https://github.com/mlgill/cheminformatics/blob/michelle/cluster_quality_metrics/demo-validate_resultes.ipynb), there are some odd inconsistencies with the results of the GPU version that need to be debugged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee524fc00eb2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.