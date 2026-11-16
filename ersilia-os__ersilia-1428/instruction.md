# Issue

**Title:** Add detailed docstrings and usage examples to Ersilia'a core modules

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [ ] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [ ] Have you successfully ran tests with your changes locally?

**Description**

This PR improves the documentation of several core module files (e.g., `model.py`, `modelbase.py`, `session.py`, etc.) by adding detailed docstrings, summaries, and usage examples to their main functions(`fetch`,`serve`,`run`, and `close`). These updates aim to improve clarity and usability, providing contributors as well as users with better guidance on how to improve and use(the API's) the commands and their various options.

Related to #1423

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bbbf1f0e6449`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.