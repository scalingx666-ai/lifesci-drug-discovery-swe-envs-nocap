# Issue

**Title:** Use `PositiveIndexKernel` as default transfer learning kernel

## Description

- Add `_extra_gpytorch_kwargs` hook to Kernel base class for injecting hardcoded constructor arguments (without exposing them as attrs fields)
  - Set `unit_scale_for_target=False` via hook in `PositiveIndexKernel` to disable botorch's target-task normalization (this way `PositiveIndexKernel` can work with an arbitrary number of tasks)
  - Switch `BayBETaskKernelFactory` from `IndexKernel` to `PositiveIndexKernel`
  - Extend `validate_gpytorch_kernel_components` to verify extra kwargs

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `611a52c61443`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.