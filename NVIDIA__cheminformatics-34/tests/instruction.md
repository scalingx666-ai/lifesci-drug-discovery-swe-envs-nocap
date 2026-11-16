# Issue

**Title:** Bugfix: CPU Clustering workflow failure from UI...

## Description

CPU UMAP modules accepts dash, but the returns np.array. In this type conversion metadata, index and partition information is lost. Though there are ways to rebuild most of this lost information, but doing this accross two datastructure and maintaining relationship is complex and costly.

This change removes dash dataframe during UMAP computation.

Other changes include:
- Raising exceptions from unimplemented method
- Pass number of partition(s) while fetching head of a dask array to avoid loading the entire cache.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a593bf014bb1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.