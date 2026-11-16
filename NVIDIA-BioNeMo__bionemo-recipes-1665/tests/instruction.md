# Issue

**Title:** fix: remove deprecated target_device argument from gather_uneven_dtensor_to_full_tensor

## Description

## Root Cause

The scheduled CI run  failed in `test_final_model_save_mfsdp` with:

```
TypeError: gather_uneven_dtensor_to_full_tensor() got an unexpected keyword argument 'target_device'
```

The `megatron_fsdp.uneven_dtensor.gather_uneven_dtensor_to_full_tensor` function no longer accepts a `target_device` parameter. It now returns a replicated DTensor instead of a full tensor on a specific device.

## Fix

1. Removed the deprecated `target_device=torch.device('cpu')` argument
2. Added `.to('cpu')` after `.to_local()` to move the gathered tensor to CPU

## Affected File

- `recipes/esm2_native_te/checkpoint.py` (line 323)

## Verification

Commit `462d94e0` is GitHub-verified with SSH signature from svc-bionemo.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `66c150f2920d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.