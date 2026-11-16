# Issue

**Title:** The smallest ring size is 3.

## Description

A minor tweak to #1317, the smallest ring size is 3 so ``[x2]`` for example should be ``[R0]`` or ``[!R]`` which is ``IS_IN_CHAIN``. We could also handle this in the parser but that would not cover manually created expressions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0485e0d1129`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.