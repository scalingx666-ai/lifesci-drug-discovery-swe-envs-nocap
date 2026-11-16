# Issue

**Title:** Reduce memory usage of the becke weights

## Description

These are the least invasive changes that fix the problem, i.e. by manually chunking before running the vectorized code and by adding a few del statements to Python's garbage collector.

The performance overhead on my test case is about 7%. Performance can be improved by using dask to parallelize over chunks but I did not want to add dask as a dependency.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `97aa04fa6e4f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.