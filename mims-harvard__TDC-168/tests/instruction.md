# Issue

**Title:** fix: dynamic oracle loading (sklearn version)

## Description

Addresses #163 

This is a draft PR with a rough sketch. Let's discuss here :) 

- Draft PR for dynamic loading of oracles dependent on `sklearn` version.
- Idea: Determine the sklearn version at runtime. Then, load the correct version of the oracle, i.e., the one that was trained with the sklearn version that the current user has. Disadvantage: Users with different sklearn version will see slightly different predictions for the same Oracle-smiles pair.
- The idea would be to just append a `_sklearn>024` to the filename of the original model on your COS
- This should be minimally invasive as it is perfectly backwards compatible and does not have side effects


TODO:
- [ ] I do not know the codebase well enough to see whether this sklearn versioning problem might arise in other places of the package as well.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4c783ff1ae39`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.