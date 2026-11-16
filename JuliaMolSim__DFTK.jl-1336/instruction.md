# Issue

**Title:** Implementation of the hybrid preconditioner for ferromagnetic systems

## Description

This pull requests implements a new preconditioner meant for magnetic systems, that is based on a diagonal model for the non-interacting susceptibility (https://hal.science/hal-05658631).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c667d68dfe99`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.