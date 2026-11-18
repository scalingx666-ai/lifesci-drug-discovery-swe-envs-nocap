# Issue

**Title:** Tighter cutoff

## Description

Tighten default cutoffs.

1) CUTOFF           1.0d-7       ->         1.0d-10
2) XCCUTOFF      1.0d-7      ->         1.0d-8

- Introduced finer cutoff for basis sets with diffuse basis functions (multiply both CUTOFF and XCCUTOFF by 0.1)
- Primlimit is now made tighter along with integral cutoff in adjust_cutoff
- TIGHTINT and COARSEINT settings are made finer.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cc2c1cbb3322`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.