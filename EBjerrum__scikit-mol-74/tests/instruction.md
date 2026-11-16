# Issue

**Title:** fix deprecation warning for DataFrame.swapaxes

## Description

This PR fixes deprecation warnings about `DataFrame.swapaxes`, detailed in #49.

This deprecation warning arises from calling `np.array_split()` on a DataFrame. Unfortunately it will not be fixed between numpy and pandas, as detailed in  It seems that in the future it may return ndarrays instead of DataFrames.

The fix here is one possible implementation: for pandas objects, split the integer index values, then apply them to the pandas object using `iloc`.

Thanks for the great package, by the way!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f5b1dba185e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.