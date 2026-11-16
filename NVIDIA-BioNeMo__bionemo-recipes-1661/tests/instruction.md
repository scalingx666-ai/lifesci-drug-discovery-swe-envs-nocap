# Issue

**Title:** fix: remove deprecated target_device argument from gather_uneven_dtensor_to_full_tensor

## Description

The megatron_fsdp.uneven_dtensor.gather_uneven_dtensor_to_full_tensor function no longer accepts a target_device parameter. It now returns a replicated DTensor instead of a full tensor on a specific device.

Fix by:
1. Removing the target_device=torch.device("cpu") argument
2. Adding .to("cpu") after .to_local() to move the gathered tensor to CPU

This fixes the TypeError: gather_uneven_dtensor_to_full_tensor() got an unexpected keyword argument "target_device" error in test_final_model_save_mfsdp.

Related to failed nightly CI run #28019158813.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a1d3ccce577e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.