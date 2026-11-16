# Issue

**Title:** Add missing endpoint for general dataset status

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

The client has a function `get_dataset_status_by_id` which allows you to get the status of a dataset without getting the dataset itself. This is useful if you have lots of datasets you are watching. However, the API endpoint was missing. This add that endpoint (and a test).

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2cafd6a6a5c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.