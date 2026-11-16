# Issue

**Title:** Fix symmetries, round 2: uniform scaling

## Description

@niklasschmitz realized that symmetries were incorrectly being filtered out for a uniform scaling. The simplest fix would have been to replace `wcart = A0 * w` by `wcart = A*w`, but we took this chance to fix the filtering such that it doesn't need access to primal values, in preparation for higher-order implementation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `38b7f27778ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.