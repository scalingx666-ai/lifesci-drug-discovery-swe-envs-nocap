# Issue

**Title:** Fix pandas 3.0 breakage in evo2_phage_gen unit tests and evo2_megatron LoRA notebook

## Description

## Summary

Fixes the CI failures from [run 34333760308](https://github.com/NVIDIA-BioNeMo/bionemo-recipes/actions/runs/34333760308) (`unit-tests (recipes/evo2_phage_gen)` ×4, `notebook-tests (evo2_megatron)` ×1, plus the `verify-recipe-tests` aggregate). The failing jobs resolved the unpinned `pandas` dependency to **3.0.5**, and three pandas-3.0 breaking changes are responsible:

- **`recipes/evo2_phage_gen/.../reward.py`**: `_set_row_values` created missing columns with a `""` placeholder, which pandas 3 infers as a strict `str` dtype. Assigning the float `reward_safety_penalty` then raised `TypeError`, which the broad `except` in `add_sequence_safety_rewards` swallowed — leaving scanned rows at the unavailable defaults (empty `safety_scan_record_id`, zeroed safety rewards). This was the single cause of the three `test_reward.py` failures.
  - Add the missing `reward_safety_penalty: 1.0` to the unavailable-path defaults (unavailable ⇒ gate not passed ⇒ full penalty, consistent with the `_aggregate_reward` recompute).
  - Keep the `_set_row_values` fallback column object-dtype so future non-string telemetry fields can't hit the same dtype trap.
- **`recipes/evo2_phage_gen/.../test_nemo_rl_env.py`**: pandas 3's inferred `str` dtype rejects lone surrogates at DataFrame construction, so `test_scored_records_exclude_full_sequence_from_rollout_metadata` failed before exercising the sanitizer. Build the invalid-unicode probe as an object-dtype column instead.
- **`recipes/evo2_megatron/.../lora-fine-tuning-tutorial.ipynb`**: pandas 3 finalized the 2.2 deprecation — `groupby("label").apply(...)` no longer passes the grouping column into the lambda, so the `FAST_CI_MODE` subsample silently dropped `label` and `df.itertuples()` rows lost `.label` (`AttributeError: 'Pandas' object has no attribute 'label'`). Select all columns explicitly per the documented pandas 2.2 migration path.

All changes remain pandas-2.x compatible.

## Testing

Reproduced all failures in a clean venv with pandas 3.0.5, then verified with the fix:

- All 4 previously-failing tests pass; full `test_reward.py` (57 passed) and `test_nemo_rl_env.py` (38 passed, 30 skipped) suites pass
- `test_sequence_safety*.py` + `test_calibration_selection.py` pass (33 passed)
- Notebook JSON valid; the fixed `groupby.apply` + `to_jsonl` path verified end-to-end under pandas 3.0.5
- `pre-commit run` and `ci/scripts/check_copied_files.py` pass

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5fee884bbb0c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.