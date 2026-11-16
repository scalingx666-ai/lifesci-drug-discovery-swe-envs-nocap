# Issue

**Title:** Fix stack overflow in gaussformat and cube

## Description

Thanks to @damseleng for the report and	proof-of-concept

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `54e394ddaf7b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.