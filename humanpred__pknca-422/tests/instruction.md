# Issue

**Title:** 317 feat/exclusion based on adj.r.squared

## Description

@billdenney  Let me know if these changes look good to close #317 or need a modification

This PR introduces a new function, `exclude_nca_min.hl.adj.r.squared()`, to exclude results based on a minimum adjusted r-squared threshold for half-life calculations. The default threshold is set to 0.9 if not provided.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e1285fb12e1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.