# Issue

**Title:** Fix Float8CurrentScaling NaN for CodonFM: init TE layers on CUDA

## Description

## Summary

Fix nightly CI failure in `unit-tests-recipes.yml` ([run #23790357242](https://github.com/NVIDIA/bionemo-framework/actions/runs/23790357242)).

### Root Cause

`CodonFMEncoder` and `CodonFMLMHead` initialized TransformerEngine layers on `"cpu"` instead of `"cuda"` (unlike ESM2 and all other models). In `test_legacy_quantized_model_init_forward_and_backward`, the model is created inside a `quantized_model_init(Float8CurrentScaling)` context then moved with `model.to("cuda")`. Moving FP8-quantized tensors from CPU→CUDA corrupts `Float8CurrentScaling`'s scale metadata, producing NaN loss.

### Fix

Changed CodonFM's TE layer init device from `"cpu"` to `"cuda"` (matching ESM2), which is a 2-line change in `modeling_codonfm_te.py`. The initial xfail approach (commit 1) was too broad — only codonfm was affected.

### Files Changed

- `bionemo-recipes/models/codonfm/modeling_codonfm_te.py` — Fix device init (`"cpu"` → `"cuda"`)
- `bionemo-recipes/recipes/codonfm_native_te/modeling_codonfm_te.py` — Synced copy
- 5× `test_modeling_common.py` — Removed unnecessary xfail (net -1 line each)

---
*Automated fix by OpenClaw + Claude Code*

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f0d4bfdb0084`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.