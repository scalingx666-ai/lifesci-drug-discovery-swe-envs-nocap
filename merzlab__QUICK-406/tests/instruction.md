# Issue

**Title:** All types of whitespace characters used for delineation are not correctly parsed in input files

## Description

When locating blocks in put file, previously a tab was not being considered as a space.

Now, if a line contains only tabs and/or spaces its considered an empty line.

The issues in the test set related to external charges with a tab at the end of the file as a newline is now fixed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dad252a2924c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.