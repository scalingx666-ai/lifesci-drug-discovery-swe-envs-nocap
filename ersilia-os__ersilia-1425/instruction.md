# Issue

**Title:** Update Issue Template to Remove Auto-Assignment

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [x] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [x] Have you successfully ran tests with your changes locally?

**Description**

This PR removes the assignees' field from the issue template to prevent auto-assigning @DhanshreeA to all new tasks. With this update, assignments will be done manually when needed.

**Changes to be made**

Remove the assignees field in Epic, Task and Batch.

**Status**

Issues assignment now manual

**To do**

Related to

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ab18d7762d54`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.