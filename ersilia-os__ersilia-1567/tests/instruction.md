# Issue

**Title:** pre commit fixes

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [x] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [x] Have you successfully ran tests with your changes locally?

**Description**

Improved template resolver to use FastAPI as a prioritary option and deal with FastAPI versions.

**Status**
Done

Is this pull request related to any open issue? If yes, replace issueID below with the issue ID

Related to #1562

_Copilot generated text below_

This pull request introduces several changes to the `ersilia` package, focusing on enhancing FastAPI support, improving error handling, and adding new utility functions. Here are the most important changes:

### Enhancements to FastAPI support:
* Added `FASTAPI_APPROVED_PYTHON_VERSIONS` to the list of approved Python versions in `ersilia/default.py`.
* Updated `is_fastapi` method in `ersilia/hub/fetch/actions/template_resolver.py` to include additional checks for required files and validate the Python version specified in the Dockerfile.

### Error handling improvements:
* Introduced a new exception class `WithToolFetchingNotWorking` in `ersilia/utils/exceptions_utils/fetch_exceptions.py` to handle cases where fetching with specific tools fails.
* Updated `_fetch_not_from_dockerhub` method in `ersilia/hub/fetch/fetch.py` to raise `WithToolFetchingNotWorking` when fetching with FastAPI or BentoML fails.

### Utility function additions:
* Added `_less_on_file` method in `ersilia/hub/fetch/register/standard_example.py` to read and format a CSV file for logging purposes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4d76c286a67c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.