# Issue

**Title:** Fix isotope hessian

## Description

## Fixes issue #1143 

### Problem

- Isotope masses were overridden by physical values.

### Fix

- shift initialization of atomic masses directly to line directly after allocation of the array `atmass` (see `init_split`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `12fcd37a3985`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.