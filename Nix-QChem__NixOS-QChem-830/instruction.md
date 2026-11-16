# Issue

**Title:** psi4: add patch for libint+pybind compatibility

## Description

This fixes the pybind11 compatibility issues we will face with libint2 usage in Psi4 in the next update to nixpkgs-unstable. It mainly adds the headers that were implicilty used before.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `07252d4edece`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.