# Issue

**Title:** Add Hessian to C-api

## Description

Adds an API interface to the calculator type's `hessian` method. Unlike the underlying method, the parameters (e.g. step size and list of atoms to include) and other return values (dipole gradient) are all optional.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bdc305f462ee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.