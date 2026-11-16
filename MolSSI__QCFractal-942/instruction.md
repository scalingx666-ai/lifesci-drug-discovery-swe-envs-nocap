# Issue

**Title:** Allow copying specs between datasets with same name/id

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Before, when copying specifications from one dataset to another, an error was raised if a spec with the same name existing in the destination dataset. This relaxes that a bit, allowing for the copying to succeed (or at least not error) if the underlying specification_id is the same.

This allows for easier copying of specs & records from multiple datasets with the same specification, which is common.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `daf8704f39c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.