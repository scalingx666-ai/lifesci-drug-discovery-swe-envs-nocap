# Issue

**Title:** Refactor test_transform.py

## Description

Refactored the tests inside `test_transform.py`. 
- Dropped unitest in favour of pytest. 
- Tests are now easier to read and extend.
- The only lines missing in the coverage from the `InverseRTransform`, which is deprecated and will be removed soon.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bbb0884b9555`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.