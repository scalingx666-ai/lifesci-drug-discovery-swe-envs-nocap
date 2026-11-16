# Issue

**Title:** Check for nans/infs in rdkit embedding and normalise features

## Description

The notebook is adjusted to set all nans (52) and infs (6), a total of 62 entries from ~ `17k x 201` values to `0.`. In addition, the features are normalised and columns with `std=0.` are deleted.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3c76c48c647d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.