# Issue

**Title:** Fix default arg in NEB query model

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->
Very small - fixes the default value for `program` NEBQueryFilters (should be a list, or None).

I noticed some errors on our instance related to this.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ccb126b1743f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.