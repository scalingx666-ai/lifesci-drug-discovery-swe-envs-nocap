# Issue

**Title:** Add ability to create torsiondrive dataset entries from an optimization dataset

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

For a torsiondrive dataset, add the `add_entries_from` for a torsiondrive. This allows for a dataset of optmizations to be used to create entries for a torsiondrive dataset.

Only final molecules from completed optimizations will be used to create entries, and entry names will be re-used. Only new entries will be created - existing ones will not be overwritten.

Somewhat quick and dirty, but tested and functional.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c2be9b58a429`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.