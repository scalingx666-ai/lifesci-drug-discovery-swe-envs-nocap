# Issue

**Title:** Drop Py3.8 and Py3.9, harden eval, add license check and serve close fix

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [x] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [x] Have you successfully ran tests with your changes locally?

**Description**
Drops Python 3.8/3.9 support, hardens unsafe eval usage, adds a license check to the model test suite, and fixes serve to properly shut down a previously served model.
**Changes to be made**

- Bump minimum Python to 3.10 (pyproject.toml, publish workflow, playground config).
- Replace eval with ast.literal_eval in io/input.py and utils/config.py.
- Add a Model License check to the test CheckService.
- On serve, close the previous model's container/session and deregister it before serving the new one.

**Status**

Complete and tested locally.

**To do**

_If this is a work in progress, Replace this line with your next steps_

Is this pull request related to any open issue? If yes, replace issueID below with the issue ID

Related to #1883

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a999787d5118`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.