# Issue

**Title:** Feat: Post-processing functions to normalize parameters

## Description

Changes involve:

  - Added functions to normalize PK parameters based on a column in PKNCAconc (`normalize_by_col`) or using custom normalization tables (`normalize`). 

  - Tests added to validate the behavior of normalization functions, including handling of missing groups, duplicate groups, and mismatched lengths
  
  - New vignette entry in post-processing to explain how to use these functions

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a49386aba25c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.