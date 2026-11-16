# Issue

**Title:** Test dockerhub conda install

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [x] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [x] Have you successfully ran tests with your changes locally?

**Description**

The `test-model-image workflow` was failing intermittently for some models in the `run_bash` consistency check, blocking the Docker image from being retagged as latest. After investigation, these failures were identified as false positives caused by a conda sourcing problem in the CI runner, not by actual issues with the model outputs.

**Changes to be made**

Added a `--permissive` flag to ersilia test, only active in combination with `--from_dockerhub`, that downgrades a `run_bash` failure from false to "warning" in the JSON report instead of blocking the workflow.

**Status**
Implemented and tested locally and with github workflows:

-` --permissive flag` added to CLI, ModelTester, and RunnerService
- `parse_status()` in `io.py` updated to return "warning" for WARNING statuses

**To do**

- Update test-model-image workflow in ersilia-model-workflows to pass --permissive flag

Related to

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1f315f9679ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.