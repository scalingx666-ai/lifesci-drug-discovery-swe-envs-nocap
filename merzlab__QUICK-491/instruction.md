# Issue

**Title:** Skip K accumulation for GPU 2e integrals if HF exchange fraction is zero

## Description

## Changes

### `gpu/gpu_get2e_subs.h`

Add a line in a GPU kernel function to compute J and K that skips the atomic adds that adds K when the HF exchange fraction is zero.

## Benchmarks

Benchmarks were done on morphine and taxol. See [this attached file (benchmark.tar.gz)](https://github.com/user-attachments/files/29917335/benchmark.tar.gz) for detailed benchmark information.

**Conclusion:** This change provides an approximate 1.1x speedup on consumer hardware.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4d9516d75a72`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.