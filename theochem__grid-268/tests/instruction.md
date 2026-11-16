# Issue

**Title:** Refactor ngrid

## Description

Refactored the ngrid module to improve readability and add features.

- Added weights property which returns the weights for each argument combination (due to its combinatorial nature returns a generator)
- Added points property which returns the combinations of arguments (due to its combinatorial nature returns a generator). Each point is a tuple with several arrays, each array corresponds to an argument of the multigrid function to integrate.
- Added support for non-vectorized functions. These will be evaluated point by point during the integration.

@PaulWAyers I think this PR improved the previous class. Nonetheless, I still have some doubts:
1. The current class used is a derived class of `Grid` because of this, several methods are inherited `moments`, `save` and `get_localgrid`. I think that `save` and `get_localgrid` can be implemented (I have some doubts about the meaning of `get_localgrid` in this context ), but I don't see how to get `moments`. 
2. This one is related to my previous doubt. Wouldn't be better to make a new class called perhaps `MultiDomainGridIntegrator` that is only responsible for integrating functions with more than one argument?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `090683e6ed8f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.