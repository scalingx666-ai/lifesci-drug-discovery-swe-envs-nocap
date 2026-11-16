# Issue

**Title:** Thermo submodule: make mass weighting a seperate keyword

## Description

This change separates now the input hessian format from the mass-weighting boolean in the thermo submodule. This lead in the past to confusion with issue #1333 which should be closed by this PR

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b31754bf3c7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.