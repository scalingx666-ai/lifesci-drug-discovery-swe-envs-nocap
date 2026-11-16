# Issue

**Title:** Serve time rdkit and other package installation

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [ ] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [ ] Have you successfully ran tests with your changes locally?

**Description**

To make the run CLI even faster, we can install packages at serve time. This PR enable package installation at the serve time that enable fast run CLI session.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb0ce9876ad9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.