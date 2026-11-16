# Issue

**Title:** Change Windows test mode from 'latest' to 'stable'

## Description

Probably a copy/paste mistake when I changed how the test matrix is produced...

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c6429ad162cf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.