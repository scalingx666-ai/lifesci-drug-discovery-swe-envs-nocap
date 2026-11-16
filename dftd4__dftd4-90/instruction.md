# Issue

**Title:** Support dispersion properties in QCSchema runner

## Description

- allow `property` keyword in `run_qcschema`
- install `parameters.toml` and add `dftd4.parameters` module to process them

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fa8dfb9c4ab4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.