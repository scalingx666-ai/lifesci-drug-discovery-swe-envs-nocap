# Issue

**Title:** Fix T008 under windows

## Description

## Description
The CI does not get green because of too many requests in T008 under windows. This PR aims to fix this

## Todos
- [x] add time.sleep to rcsb requests
- [x] fix T008
- [x] all tests pass

## Others
- [x] exclude two links from CI DOCS broken link tests

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6c5e61df5e0f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.