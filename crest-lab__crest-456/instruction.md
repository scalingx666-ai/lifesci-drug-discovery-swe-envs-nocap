# Issue

**Title:** 3.0.2 maintenance

## Description

A small refactor of the GitHub workflows plus:
-  adding alias for `--cinp`: `-C`/`-c`
- position independent input file readout from cli
- Update of the `tblite` submodule to its version 0.5.0
- activation of pre-optimization when selecting search runtypes via toml
- `-grad`/`-nograd` flags for `--sp` runtype.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `163f50a913f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.