# Issue

**Title:** create dc_torch_restore() fcn for cpu compatibility

## Description

Use separate model.restore() function in order to force a GPU trained model to work on a CPU machine

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `00933605b247`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.