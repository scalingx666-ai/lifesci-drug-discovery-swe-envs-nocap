# Issue

**Title:** Dataset similarity

## Description

- Add new class that performs k-nearest neighbor searches using
          Tanimoto similarity. The implementation uses sparse dot product
          making the algorithm 2-3x faster than RDKit's BulkTanimotoSimilarity
 - Add notebook illustrating NearestNeighborsRetrieverTanimoto for
          dataset similarity analysis, like train/test set comaparison.

Also addresses

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cee9288926d5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.