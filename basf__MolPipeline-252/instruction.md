# Issue

**Title:** Remove legacy functions in main

## Description

Same changes as in  which merged to `development`.  
Since the key features required to merge dev are a bit stalled, I try to integrate as much as possible in main, so the overhead stays as small as possible when merging dev.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `daa1afba3e50`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.