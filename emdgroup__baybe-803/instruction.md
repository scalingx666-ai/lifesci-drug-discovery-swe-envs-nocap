# Issue

**Title:** Enable Pandas 3

## Description

Main changes explained:
- pandas 3 now uses `Copy on Write` (CoW) which can cause trouble in some code parts, mostly where we used `df.values` before by causing torch warnings about undefined behavior on read-only arrays. I've generally followed different approaches depending on the context:
  - where we previously used `torch.from_numpy(df.values)` or similar, we cant do this any longer because `values` might be read-only. In places where the array is definitely small (eg when talking about bounds) I am using now `df.to_numpy(copy=True)` as it always ensures a copy and thus writeability
  - other places deal with potentially large arrays. Here I am reading out this pattern `if not array.flags.writeable: array = array.copy()`
- `df.values` apparently can now also return something of type `ArrowStringArray` (eg for strings). This cannot be handled in some downsteam parts etc, so it is converted (eg to list) where needed
- The `Dummy` class that was used in the invariance constraint was remove and a different approach that uses `None` as sentinel is used now

Pandas 3 is only supported for Python 3.11+ so the 3.10 test serves as a verification that everything (still) works in Pandas 2

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f59151e2cc43`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.