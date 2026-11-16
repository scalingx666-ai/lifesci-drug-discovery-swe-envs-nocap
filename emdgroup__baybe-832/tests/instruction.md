# Issue

**Title:** Recommendation Dataframes

## Description

Refactors the return types of the discrete recommendation engine, as a preparation for #793.

The `pd.Index` returned by `_recommend_discrete` and its helpers has two structural downsides:
- It is hard-wired to pandas index semantics (#795)
- It implicitly assumes a fully materialized search space, which does not scale (#796)

Switching to returning a `DataFrame` subselection directly is the natural fix – and it is straightforward to achieve because the intermediate index was never necessary in the first place: the helpers already have `candidates_exp` in scope and callers were simply using the index to re-select the same rows immediately after. It is a legacy mechanism from times where search spaces tracked recommendation metadata.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `feef29b2e5c0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.