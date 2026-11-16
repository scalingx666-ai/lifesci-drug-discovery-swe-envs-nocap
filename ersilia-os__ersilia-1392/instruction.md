# Issue

**Title:** Logging at realtime from the async subprocess while pulling

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [x] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [x] Have you written new tests for your core changes, as applicable?
- [x] Have you successfully ran tests with your changes locally?

**Description**

This PR enhances the `async_pull` method by adding real-time logging for Docker subprocess commands. The changes improve debugging and provide better insight into the progress of `docker pull` operations.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `98618b70ca49`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.