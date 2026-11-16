# Issue

**Title:** Support UTF-8 paths on Windows (allow for non-ASCII characters in paths)

## Description

These changes make it possible to load files with special UTF-8 characters (e.g., é, à, ö) in their paths on Windows.

The tests pass.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8b7066189063`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.