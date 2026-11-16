# Issue

**Title:** prevent charge.py doctest erroring when HTMD_CONFIG is defined

## Description

This happens on deployment sites where `HTMD_CONFIG` is defined and the doctest errors because htmd import is no longer silent. Not urgent, but annoying.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3fee7d9ea7ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.