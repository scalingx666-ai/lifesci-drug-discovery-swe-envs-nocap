# Issue

**Title:** Only interpolate when BS branch has more than 2 datapoints

## Description

This is a fix for issue #123 ran into the same error, and found that it occurs when a bandstructure branch has 1 datapoint, and so `interp1d` throws an error, because it makes no sense to interpolate one datapoint.

Tested and fixes the issue.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c4496bb76b99`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.