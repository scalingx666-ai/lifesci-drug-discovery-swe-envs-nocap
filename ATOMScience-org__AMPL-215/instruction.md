# Issue

**Title:** Update diversity_plots.py

## Description

fix the tanimoto distance plot to reflect the nearest neighbor distance instead of all distances. It was erroneously changed previously and just needs to be changed back to what it was before.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c6faee53cf4c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.