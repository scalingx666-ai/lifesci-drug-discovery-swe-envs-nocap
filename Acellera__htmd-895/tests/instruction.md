# Issue

**Title:** ACEMD3 integration with tests and dependency

## Description

- [x] updated protocol tests
- [x] added functional acemd3 tests
- [x] added HTMD dependency on acemd3 >= 3.2.0

Need to wait for the official 3.2.0 release before this can pass the tests

Related data PR:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf3b54b44639`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.