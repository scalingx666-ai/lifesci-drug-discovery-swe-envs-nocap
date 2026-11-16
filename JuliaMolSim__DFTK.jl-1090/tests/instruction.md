# Issue

**Title:** Fix occupation insulator

## Description

Fix #1089 by making sure large band gap + temperature returns a sane Fermi level and the insulator branches are taken for chi0 computations.

TODO:
- [x] Convert issue example into test within the response calculation tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `01c245ae21ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.