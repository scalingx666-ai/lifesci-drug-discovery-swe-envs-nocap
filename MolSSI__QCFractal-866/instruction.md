# Issue

**Title:** More helpful error message on errors with snowflake import of qcfractalcompute

## Description

## Description
Very minor improvement related to Issue #864 

There, the parsl  import error would be caught by the snowflake module and be interpreted as a missing `qcfractalcompute` package. This does a test for the existence of the `qcfractalccompute` package first, and then passes along any other import errors

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `16a504899333`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.