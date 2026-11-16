# Issue

**Title:** Refactor partial charges

## Description

- [x]  Create `htmd.charge` submodule
- [x] Create `fitGasteigerCharges` function
  - [x] Tests
- [x] Create `fitESPCharges` function
  - [x] Move `ESP` class to `htmd.charge`
  - [x] Tests
- [x] Refactor `main_parameterize` function
  - [x] Add `--charge-type` flag
  - [x] Tests

Depend on 

Fix #510

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `04d1a47242cc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.