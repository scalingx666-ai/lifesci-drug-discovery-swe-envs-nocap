# Issue

**Title:** fix: binray splitting, input missing in output, string wrapper issue

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [ ] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [ ] Have you successfully ran tests with your changes locally?

**Description**
- [x] Added binary splitting logic when one smiles fail
- [x] Fix for incorrect smiles being filtered out
- [x] Removing the string wrapper
- [x] Adding a check to see if the input and the output matched 
- [x] BaseInformation field validation in the test command
- [x] Cleaning up the model when they produce empty result during fetching.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `87e82e5a42bc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.