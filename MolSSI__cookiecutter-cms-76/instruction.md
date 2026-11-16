# Issue

**Title:** Fix so that CookieCutter does not fail with no windows CI

## Description

This PR addresses issue #75.

The issue itself was fixed by removing a reference to a conda build for windows continuous integration. 

I've also added tests for no Windows CI to travis (maintainers can decide if they'd like to include these).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b7069aecd972`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.