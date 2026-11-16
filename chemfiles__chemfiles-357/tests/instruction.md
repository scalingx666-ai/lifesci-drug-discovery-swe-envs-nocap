# Issue

**Title:** Speedup OS X gcc CI build by not re-installing everything

## Description

It is much slower than other builders for an unknown reason

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f9d745a97c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.