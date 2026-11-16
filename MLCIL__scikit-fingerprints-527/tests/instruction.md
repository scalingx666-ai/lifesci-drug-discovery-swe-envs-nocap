# Issue

**Title:** Expand random_state type hints to accept RandomState

## Description

## Summary
- Expanded `random_state` parameter type annotations from `int | None` to `int | np.random.RandomState | np.random.Generator | None` across 5 files, aligning with scikit-learn conventions
- Skipped `conformer_generator.py` (RDKit only accepts `int`) and `maxmin_split.py` (same RDKit limitation)
- `randomized_scaffold_split.py` already had the broad type and was left unchanged

## Files changed
- `skfp/bases/base_fp_transformer.py`
- `skfp/bases/base_substructure_fp.py`
- `skfp/fingerprints/e3fp_fp.py`
- `skfp/fingerprints/map.py`
- `skfp/model_selection/hyperparam_search/randomized_search.py`

## Test plan
- [x] `pytest tests/ -k "E3FP or MAP"` — all 14 selected tests pass
- [x] No functional changes, type hints only

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `533a42ee4941`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.