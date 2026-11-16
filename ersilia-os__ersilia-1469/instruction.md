# Issue

**Title:** Legacy bentoml dockerfile python version upgrade

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [ ] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [ ] Have you successfully ran tests with your changes locally?

**Description**

Changing the python version from python 3.7 to 3.10 to be compatible with `aiohttp` package in docker building on both `multistage` and `legacy-bentoml`.

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e3510ee710c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.