# Issue

**Title:** Additional checks if dataset records aren't able to be fetched

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

If a particular entry/specification does not exist in a dataset, `get_record` can end up trying to access elements of a list that don't exist. This fixes that with some additional checks

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e8efc67436d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.