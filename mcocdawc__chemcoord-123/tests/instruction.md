# Issue

**Title:** Small fixes

## Description

- use `arctan(x, y) == arctan(x / r,  y / r)` for non-zero r and get rid of unnecessary division. Spotted by @nwhel 
- added missing rst files for the new pyscf conversion methods.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `651ddc01d30a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.