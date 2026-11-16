# Issue

**Title:** Enhancement for providing representations.

## Description

Currently, the initial representations (if provided) is only applied after the default representation is executed. This change makes sure to set `default_representation` to False.

Also adding `center` keyword (user might not want to 'center' at all).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8b16a516b0bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.