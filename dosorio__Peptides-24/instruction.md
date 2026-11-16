# Issue

**Title:** remove leading white spaces in data lines

## Description

after last fix, if there are white spaces in the beginning of data lines, it will lead to a empty element in the data frame. This is error-prone, especially if not every data line has white spaces in the beginning. Now remove white spaces around each data line.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0ab55fde205d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.