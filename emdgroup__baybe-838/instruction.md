# Issue

**Title:** Refactor recommendation mechanics

## Description

*This is a pure internal refactor — no behavior change.*

### Background

The consistency of the attribute structure of `SubspaceDiscrete` was historically enforced only by convention, not by the type system, meaning that mutating a subspace instance could produce an inconsistent state. Creating filtered copies of a subspace was therefore not safe. On top of that, doing so could have been potentially costly, since it might have involved materializing (parts of) the Cartesian product — another reason to avoid it.

As a workaround, the codebase avoided modifying subspace objects for filtered candidate sets altogether and instead computed candidates externally, threading them as a separate `candidates_exp` dataframe argument down through multiple layers of the recommender call stack. The `FilteredSubspaceDiscrete` subclass existed for the same reason: to apply a Boolean mask at call time without touching the subspace itself.

Previous preparatory PRs resolved issue  by making the consistency of the attribute structure of `SubspaceDiscrete` an enforced invariant, which now enables safe creation of filtered subspace copies. The cost problem — to be avoided by lazy materialization of the Cartesian product () — has not yet been addressed but will be resolved in a subsequent PR on the same development branch. This PR capitalizes on the invariant enforcement to simplify the recommender internals.

### Changes

**Drop `FilteredSubspaceDiscrete`** (`baybe/searchspace/_filtered.py` deleted)
The subclass existed solely to override `get_candidates()` with a Boolean mask applied at call time. Now that creating a filtered copy of a subspace is safe, the class is unnecessary. `Campaign` is updated to create filtered subspace copies directly.

**Drop dead `pending_experiments` argument**
The `pending_experiments` parameter had been used in `PureRecommender._recommend_with_discrete_parts` to filter pending experiments from the candidate set, but became dead code when that filtering responsibility was moved to `Campaign` in an earlier refactor. It is now removed.

**Drop redundant `candidates_exp` argument**
The filtered set of discrete candidates was fetched once and then passed as a parallel `candidates_exp` dataframe through several layers of the recommender stack (`_recommend` → `_recommend_discrete/hybrid` → BoTorch-specific helpers). With safe subspace mutation now available, subset-constrained paths are updated to create filtered copies of the subspace instead of propagating a separate dataframe. The argument is removed from all affected signatures across:

- `PureRecommender._recommend_discrete` / `_recommend_hybrid`
- `BotorchRecommender._recommend_discrete` / `_recommend_hybrid`
- `recommend_discrete_with_subsets` / `recommend_discrete_without_subsets`
- `recommend_hybrid_with_subsets` / `recommend_hybrid_without_subsets`
- `SKLearnClusteringRecommender._recommend_discrete`
- `FPSRecommender._recommend_discrete`
- `RandomRecommender._recommend_hybrid`
- `NaiveHybridSpaceRecommender`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2bc056ee5136`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.