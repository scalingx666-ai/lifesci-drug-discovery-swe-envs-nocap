# Issue

**Title:** Faster record count in dataset list

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

When listing datasets, the number of records in that dataset is also given. This is currently done via a large query that has to union between the different dataset types. This implements a separate table that tracks how many records are in a dataset.

The only two operations that affect the record count is submitting records and removing records. So this should be kept accurate. But we will see if we also need to have a periodic refresh that corrects any drift.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4ddef7b95f0b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.