# Issue

**Title:** feature/ipickering/improve memory efficiency

## Description

Major improvement in memory efficiency, around ~40%, by using `madvise` to release memory held by the mmaped arrays.

In the future it would be a good idea to support pyarrow parquet format, this would make things significantly simpler.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `28bf578cfd80`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.