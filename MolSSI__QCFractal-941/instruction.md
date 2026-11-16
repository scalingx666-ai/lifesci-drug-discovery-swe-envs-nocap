# Issue

**Title:** Allow entries/specs that exist to be skipped

## Description

## Description
When copying records, specifications, or entries from one dataset to another, if a specification or entry already exists there is an error. This PR changes the behavior so that if an entry or spec exists, it is skipped to avoid an error and a warning is given to a user.

## Status
- [X] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `daf8704f39c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.