# Issue

**Title:** fix(recipes): remove deprecated fully_shard() kwargs

## Description

## Summary

Remove deprecated `fully_shard()` keyword arguments that were removed in a recent megatron-core update.

### Changes
- **vit/train.py**: Remove `grad_reduce_in_fp32` and `preserve_fp32_weights` from `fully_shard()` call
- **vit/config/defaults.yaml + vit_base_patch16_224.yaml**: Remove orphaned config keys
- **esm2_native_te/hydra_config/defaults.yaml**: Remove `check_for_nan_in_grad`, `grad_reduce_in_fp32`, `preserve_fp32_weights`
- **geneformer_native_te_mfsdp_fp8/hydra_config/defaults.yaml**: Same

### Root Cause

The installed megatron-core in CI has updated `fully_shard()` API, removing these parameters:
- `grad_reduce_in_fp32`
- `preserve_fp32_weights`
- `check_for_nan_in_grad`

These were simple removals — no replacement mechanism needed for the affected recipes.

Fixes  (partially — the `nvidia-resiliency-ext` version mismatch is a container image issue requiring an image rebuild)

### Testing

- Pre-commit passes on all changed files
- Import verification confirms `fully_shard` loads without the removed kwargs

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `85a8dcc294c4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.