# Issue

**Title:** An update to initial information print

## Description

In this PR, I have updated the print statements that print version and author list into the output file. Specifically, I added pipe symbols into each line to prevent them from being considered for test vs reference output file comparisons in the test suite. This should fix QUICK test failures due to version mismatches in the AmberTools test suite.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a1e3802659c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.