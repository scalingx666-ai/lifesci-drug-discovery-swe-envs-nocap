# Issue

**Title:** staging: fix fallout from latest nixpkgs-staging merge

## Description

Fix build failures from latest nixpkgs-stagign merge.

* gamess-us: build with gfortran-14

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bbbb334aaa0a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.