# Issue

**Title:** Implement basic QCSchema support

## Description

- [x] allow running `xtb` from QCSchema input
- [x] more tests regarding energy, hessian and properties driver
- [x] report output from `xtb` API back to `AtomicResult`
- [x] documentation on this extension

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ed99e7b0224f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.