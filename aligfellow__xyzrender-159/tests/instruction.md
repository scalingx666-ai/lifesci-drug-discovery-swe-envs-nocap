# Issue

**Title:** Avoid cutting molecules across periodic boundaries

## Description

Add option to move atoms in the unit cell so that molecules are not cut across periodic boundaries.

Default behaviour:

<img width="479" height="800" alt="roy" src="https://github.com/user-attachments/assets/8fe1b0bd-0fa3-4306-a654-e0dc98e70b56" />


With '--whole' flag on:

<img width="419" height="800" alt="roy" src="https://github.com/user-attachments/assets/d335d4ef-204e-4a6d-a386-f0fddc99e123" />

The feature includes:

- make_whole() function

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e2c4b4a88202`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.