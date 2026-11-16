# Issue

**Title:** Cache Graph Isomorphism

## Description

## Description

Add `multirmsd_isomorphic` function to cache the graph isomorphism. Caching can be turned off with the `cache=False` argument.

![time](https://user-images.githubusercontent.com/11348981/74280689-ed0da300-4d14-11ea-9850-278b137167d7.png)

Caching makes `spyrmsd` much faster in most cases (`28.25` ms on average with cache versus ` 143.24` ms on average without cache, for the first 75 systems) but it's still an order of magnitude slower than `obrms` (`6.74` ms on average).

Solves #11.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0d093591c6f1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.