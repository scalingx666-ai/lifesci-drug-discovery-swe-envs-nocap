# Issue

**Title:** Move (new_)compute_tag,priority handling to top-level modify_records in Dataset

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Move where the deprecation of `tag` and `priority` arguments happens in datasets. Before, it happened in an internal `_modify_records` function, but it's better at the user-facing level (which is the only time that the internal `_modify_records` function is called with compute tag/priority arguments



## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5735f6503e98`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.