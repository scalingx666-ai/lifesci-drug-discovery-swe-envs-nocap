# Issue

**Title:** fix(ci): repair nightly recipes failure - add get_extended_attention_mask to NVEsmPreTrainedModel

## Description

## Root Cause

The nightly `unit-tests-recipes.yml` workflow (run [34459659265](https://github.com/NVIDIA-BioNeMo/bionemo-recipes/actions/runs/34459659265)) failed with `AttributeError: 'NVEsmModel' object has no attribute 'get_extended_attention_mask'` across multiple test jobs:
- `unit-tests (recipes/esm2_accelerate_te)`
- `unit-tests (models/esm2)`
- `unit-tests (recipes/esm2_native_te)`
- `unit-tests (recipes/esm2_peft_te)`

The `NVEsmModel.forward()` method calls `self.get_extended_attention_mask(attention_mask, input_shape)` but this method was not defined in `NVEsmPreTrainedModel` or its parent classes.

## Fix

Added the `get_extended_attention_mask` method to `NVEsmPreTrainedModel` (the base class for all NV ESM models) with the standard transformers signature. The implementation handles 2D, 3D, and 4D attention masks and converts them to the format expected by TransformerEngine (large negative values for masked positions).

## Files Changed

- `models/esm2/modeling_esm_te.py` (source)
- `recipes/esm2_native_te/modeling_esm_te.py`
- `recipes/esm2_peft_te/example_8m_checkpoint/esm_nv.py`
- `recipes/esm2_accelerate_te/example_8m_checkpoint/esm_nv.py`
- `recipes/vllm_inference/esm2/modeling_esm_te.py`

All recipe copies are synchronized via `ci/scripts/check_copied_files.py`.

## Tests

The fix should resolve the failures in:
- `tests/test_accelerate_esm2.py`
- `tests/test_modeling_esm_te.py`
- `tests/test_train_resume.py`
- `tests/test_peft.py`

## Verification

- Commit is signed with SSH key (SHA256:o43d6/g6Ssy+ew+W7nu/xBgh68/QywuVOuHJEONSlgw)
- Commit includes `Signed-off-by: svc-bionemo <267129667+svc-bionemo@users.noreply.github.com>`
- GitHub reports commit verification: `verified: true`, `reason: valid`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `101d88b7e0b0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.