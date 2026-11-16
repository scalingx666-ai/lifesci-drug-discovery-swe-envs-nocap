# Issue

**Title:** Fix CUDA 12 GPU tests: pin gpu4pyscf-libxc-cuda12x to 0.8.1

## Description

[agent]

## Problem

The CUDA 12 GPU test jobs (`gpu-cuda12-torch212`, `gpu-cuda12-torch213`) have been failing on `main` since the gpu4pyscf 1.9.0 update (#146). There were two separate causes:

1. **`libcusolver` not found** (fixed in #156): gpu4pyscf 1.9.0 looks for an unversioned `libcusolver.so`, which the conda package doesn't ship.
2. **Native abort in libxc** (fixed here): once tests actually ran, the process died with `Fatal Python error: Aborted` (exit 134) at the first GPU libxc call in `test_grad_veff[HF]`. Running with `-s` exposed the native message, which pytest normally captures: `operation not supported`, raised in `xc_func_init_flags` inside `libxc.so`.

The CUDA 12 runners are NVIDIA A10-4Q vGPU slices, and `gpu4pyscf-libxc-cuda12x` 0.9.0 (pulled in via the `>=0.8.1` constraint of gpu4pyscf 1.9.0) aborts there. The cause was not narrowed down further than that.

## Evidence

Diagnostic CI run on this PR, with a matrix entry pinning libxc to 0.8.1 (since removed):

| Job | libxc | Result |
|---|---|---|
| `gpu-cuda12-torch212` | 0.9.0 | abort (exit 134) |
| `gpu-cuda12-torch213` | 0.9.0 | abort (exit 134) |
| `gpu-cuda12-torch213` + pin | 0.8.1 | 121 tests and 4 doctests passed |
| `gpu-cuda13-torch213` | 0.9.0 (cuda13x) | passed |

The failure could not be reproduced on a local A100 (full GPU, not vGPU), even with free GPU memory limited to match the CI slice, 6 CPUs, and glibc malloc checks.

## Changes

- Pin `gpu4pyscf-libxc-cuda12x==0.8.1` in the pixi `cuda-12` feature and update `pixi.lock` (CUDA 13 environments are unchanged).
- Pin it in the `skala-cuda12x` PyPI package through a new `@EXTRA_DEPENDENCIES@` placeholder in the shared `skala-cuda.toml` template. `skala-cuda13x` is unchanged.
- Update `test_build_release.py` for the new dependency.

## Follow-up

Both pins carry a TODO: drop them once `gpu4pyscf-libxc-cuda12x` fixes the abort on vGPU devices.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `38665693da86`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.