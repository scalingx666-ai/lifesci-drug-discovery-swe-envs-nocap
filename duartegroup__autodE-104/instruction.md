# Issue

**Title:** IDPP for NEB

## Description

by implementing the image dependent pair potential from https://arxiv.org/pdf/1406.1512.pdf

*** 
### TODO

- [x] Initial implementation
- [x] Test gradients
- [x] Test on molecule 
- [x] Run by default on `_init_from_end_points`
- [x] Update changelog
- [x] Update documentation (NEB example page)
- [x] Rebase

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `450ae611617b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.