# Issue

**Title:** Don't require an ipycluster to be running unless we're building a database

## Description

This also has a small fix to allow input files that have more than two fields per line to be parsed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `104070031a39`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.