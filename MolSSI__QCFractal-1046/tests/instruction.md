# Issue

**Title:** Fix query_dataset_records filtering by dataset_type

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Querying dataset records by dataset_type results in an error. Noticed this when looking through internal server error logs.

Very simple and non-controversial fix (use `in_` rather than equality in the sqlalchemy stmt). Will be incorporated into the release tomorrow.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c7af37017bda`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.