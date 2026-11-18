# Issue

**Title:** Fixed HIP test failures before QUICK 26.03 release

## Description

The issue was with quick_rocblas_dgemm and quick_oeproperties_module. Following are the fixes

1) quick_rocblas_dgemm
- Keep the caller-supplied lda/ldb/ldc as-is; compute buffer sizes from them directly (rb_sizea = rb_lda * rb_k, etc.).
- Replace the rocBlasInit/rocBlasFinalize global-allocator calls with per-call allocate/deallocate (host) and hipMalloc/hipFree (device), sized exactly to the current matrix dimensions.
- Upload the initial C array to device (hipMemcpy) instead of zeroing it, and change intent(out) → intent(inout).
- Handle both lower- and upper-case transpose flags ('n'/'N', 't'/'T').

2) quick_oeproperties_module
- Extend the #if defined CUDA || defined CUDA_MPIV preprocessor guards to also cover HIP and HIP_MPIV

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6606a09c363f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.