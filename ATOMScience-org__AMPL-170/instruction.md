# Issue

**Title:** defined compatible version groups. use that to decide if versions are…

## Description

- defined a list of version compatible groups
- updated the code to get the ampl version
- updated create_prediction_pipeline and create_prediction_pipeline_from_file to check if versions are compatible
- updated the tests

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `47d1e2cb7e24`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.