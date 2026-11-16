# Issue

**Title:** BUGFIX: set DOS cutoff when --no-total

## Description

A simple fix for #56 ; just calculate the cutoff as though the total-DOS is there.

It seems as good a way of defining the threshold as any other?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `75011e202a32`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.