# Issue

**Title:** Fix uninitialized optimizer status for single-atom systems (gfortran bug)

## Description

## Summary

Fix a bug in geometry optimization for single-atom systems when xTB is compiled with gfortran.

The ANCopt, FIRE, and L-ANCopt routines return immediately when `mol%n == 1`, because a single atom has no internal geometry to optimize. However, this return occurred before the output variables `fail`, `iter`, and optional `iter_needed` were initialized.

With gfortran, `fail` could therefore contain an undefined `.true.` (or equivalent) value. The caller interpreted this as a failed geometry optimization, producing a non-convergence error and a nonzero exit status. Other compilers happened not to expose the issue consistently.

## Changes

- Initialize `fail` to `.false.` and the iteration count to zero before the single-atom early return in:
  - ANCopt
  - FIRE
  - L-ANCopt
- Initialize optional `iter_needed` when present.
- Add a charged, single-atom Li⁺ optimization regression test to the Meson and CMake test suites.

The present changes should resolve #1440 

## Expected behavior

A command such as:

```bash
xtb lithium.xyz --chrg 1 --opt
```

should complete successfully.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5fb5a1c5c27e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.