# Issue

**Title:** Always use batching with ds.modify_records

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

`ds.modify_records` (and related functions) can timeout when passing lots of entries. This PR forces the use of batching even if the user wants to modify records belonging to all entries.

(Later we will add a background_modify_records)

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a7a85a4d480f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.