# Issue

**Title:** Add atom filtering (--exclude and --only)

## Description

Adds render-time atom filtering via --exclude and --only, applied after graph building so bond orders are preserved while downstream render options keep original atom numbering.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `75bca170b67a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.