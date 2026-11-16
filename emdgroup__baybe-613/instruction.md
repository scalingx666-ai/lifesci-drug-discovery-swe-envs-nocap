# Issue

**Title:** Lockfile check via pre-commit

## Description

A little quality-of-life improvement that completely automates lockfile handling

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dad7fdc02a30`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.