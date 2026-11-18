# Issue

**Title:** detect AUG- dunning basis set as diffused basis functions

## Description

quick_method_module is edited such that AUG- dunning basis set (and PC basis sets) now sets diffuse_basis_funcs to .true.

This is necessary as tighter XCCUTOFF is required for diffused basis functions.

Currently, we detect diffused basis functions only for pople, dunning, Ahlrichs and PC basis sets.

We will need to do the same for other basis functions in future.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a56153ceb6f8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.