# Issue

**Title:** Make name/type required in DatasetQueryModel

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Previously, all fields of DatasetQueryModel were optional. However, this allowed some `None` values to propagate down, causing internal server errors.

This makes those fields mandatory, since the only real purpose of this class is getting datasets by name/type

Found by @brandontton

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6d4d7eb669a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.