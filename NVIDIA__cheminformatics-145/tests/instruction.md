# Issue

**Title:** Improve application startup time...

## Description

With this change startup time for 100k molecules is down abount one min. 
Time to process 1K molecule from 43 sec to 8 sec.

Other changes are mostly formatting and comments cleanup.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a040d103f1e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.