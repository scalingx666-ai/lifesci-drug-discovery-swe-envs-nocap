# Issue

**Title:** Speedup computation of squared pairwise distances

## Description

## Description

Fix #43 by using
```
scipy.spatial.distance.cdist(A, B, 'sqeuclidean')
```
instead of computing the euclidean distance (which involves `np.sqrt`) and taking the square.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5dd826782d8f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.