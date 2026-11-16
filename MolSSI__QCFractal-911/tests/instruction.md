# Issue

**Title:** Remove some fields from datasets

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

This PR removes 3 fields from the database and models. These fields were never really used, and the `group` field causes some confusion about what it means.

The fields:

* `metadata` renamed to `extras` - `extras` was never able to be set or modified, but `metadata` is confusing
* `group` - some sort of grouping available for the dataset. Superseded by `tags` (where each dataset can have multiple tags)
* `visibility` - meant to hid datasets from public view. Never implemented

**These PR should be should be compatible with older clients for the time being**. New clients won't work with old servers. Some future version will remove the compatibility with old clients completely.

The HTTP API has not changed, and is accepting of old clients. In addition, you may still access the `metadata` field of a  the dataset class, which is transparently redirected to `extras`.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `85b51789e5ad`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.