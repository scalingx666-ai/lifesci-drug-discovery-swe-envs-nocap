# Issue

**Title:** Fix allow_zero + categorical crashing optimize_acqf_mixed

## Description

## Problem

`f563e534` added an `include_semicontinuous` flag to `Inputs.get_number_of_categorical_combinations`, and `BotorchOptimizer._determine_optimizer` passes `not is_pruning_applicable(domain)` — so that semi-continuous features (`allow_zero=True` with `lb > 0`) are resolved by the post-AF BONSAI pruning step rather than by enumerating their on/off states.

The sibling `Inputs.get_categorical_combinations` — which builds the actual `fixed_features_list` — never got the flag. So the routing decision was contradicted at list-construction time. Whenever routing lands on `OPTIMIZE_ACQF_MIXED` / `OPTIMIZE_ACQF_LIST` for some *other* reason (a categorical or discrete input, or multiple acqfs), the semi-continuous states were still enumerated, and the features got handled twice: once by enumeration, once by pruning.

Beyond the wasted work, this crashes. The all-features-off combination pins *every* tensor column, and botorch short-circuits that case in `_optimize_acqf_all_features_fixed`, which under `return_best_only=False` collapses the restart dimension to shape `(1,)`. Combinations that leave a column free return `(num_restarts,)`. `optimize_acqf_mixed` stacks these unguarded:

```
RuntimeError: stack expects each tensor to be equal size, but got [1] at entry 0 and [20] at entry 1
```

Reproduced on `main` with three `allow_zero` inputs plus one `CategoricalInput`:

```
routed: OPTIMIZE_ACQF_MIXED  combos=16  cols=4  all-fixed combos=2  -> FAILED
```

Pure categorical/discrete domains are unaffected — there *every* combination pins every column, so the list stays homogeneous and stacks fine. Only the semi-continuous enumeration mixes the two kinds:

```
2 DiscreteInput only              combos=6   cols=2  all-fixed=6/6   ok
DiscreteInput + CategoricalInput  combos=6   cols=2  all-fixed=6/6   ok
3x allow_zero + categorical       combos=16  cols=4  all-fixed=2/16  FAILED
```

## Fix

- Add `include_semicontinuous: bool = True` to `Inputs.get_categorical_combinations`, mirroring the counting function.
- `BotorchOptimizer.get_categorical_combinations` passes `not is_pruning_applicable(domain)`.
- The `n_combos` guard in the `OPTIMIZE_ACQF_LIST` branch was also calling the counting function without the flag, and would have disagreed with the list it guards; it now passes the same value.

After the fix the same domain yields `combos=2  all-fixed=0` and `ask` succeeds, with pruning still zeroing the semi-continuous features as intended.

## Tests

Three regression tests, each verified to fail without the source change:

- `test_inputs_get_categorical_combinations_exclude_semicontinuous` — data-model level; asserts the enumeration drops semi-continuous features, and that both functions agree for **both** values of the flag (the invariant that was broken).
- `test_get_categorical_combinations_excludes_semicontinuous_when_pruning` — 16 → 2 combinations, and no combination pins every tensor column.
- `test_ask_with_semicontinuous_and_categorical` — end-to-end `ask(candidate_count=2)` on the issue's domain plus a categorical, asserting each `allow_zero` feature lands on zero or inside `[lb, ub]`, never in the forbidden gap.

`tests/bofire/data_models` 1368 passed; `tests/bofire/strategies` 506 passed. The two `doe/test_utils.py::test_n_zero_eigvals_*` failures are pre-existing on a clean tree and unrelated. `ty check bofire` reports 146 diagnostics before and after.

## Follow-up (not in this PR)

The botorch side is a genuine upstream bug: `optimize_acqf_mixed` assumes every entry of `fixed_features_list` yields the same acqf-value shape. This PR stops BoFire from constructing the heterogeneous list that triggers it, but the latent issue should be filed upstream so it can't resurface from another direction.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58f01b2e9d21`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.