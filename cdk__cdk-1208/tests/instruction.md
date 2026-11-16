# Issue

**Title:** Add InChI AuxInfo to structure functionality;

## Description

I noticed that the ‘AuxInfo to structure’ function was missing. So I implemented it, adapted the existing code to avoid duplicates, and added tests.
Please let me know what you think.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `441d1832449a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.