# Issue

**Title:** Reduced code complexity and fixed a bug

## Description

There's a bug where timed out MSA submission requests from the mmseqs2 API result in an infinite loop since the error count code is not properly referenced.

This PR addresses that bug and reduces some unnecessary code as well.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a9b3abc2c1f9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.