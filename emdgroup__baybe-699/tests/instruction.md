# Issue

**Title:** Validate dataframe content against `active_values`

## Description

Fixes .

Problem: The `SearchSpace.from_dataframe()` method does not automatically respect `active_values` when constructing search spaces. This causes the method to include all dataframe rows, even those containing non-active values.

Solution: Add validation to detect when a dataframe contains rows with non-active values and raise an `IncompatibilityError`. 

  Changes:
  - Add validation logic to detect `active_values` violations
  - Raise `IncompatibilityError` 
  - Add simple test
  - Update CHANGELOG.md

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `145cc8a99aa1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.