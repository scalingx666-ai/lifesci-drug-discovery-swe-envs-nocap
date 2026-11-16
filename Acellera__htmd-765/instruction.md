# Issue

**Title:** improved ensurelist to support ranges

## Description

Fixes a bug where passing a `range` (not `np.arange`) to `ensurelist` returned a list with the range inside instead of a list of the elements of the range.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `06930b00aaa8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.