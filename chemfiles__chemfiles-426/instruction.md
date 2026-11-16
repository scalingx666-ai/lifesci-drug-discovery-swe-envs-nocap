# Issue

**Title:** fix(DCD): read frames with missing unit cell data

## Description

Molfile now defaults to all lengths set to zero. Did some quick tests and this does not seem to interfere with anything.

Depends on 

Might fix #419.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7344020b331b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.