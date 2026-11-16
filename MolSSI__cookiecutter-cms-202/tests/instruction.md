# Issue

**Title:** Update license metadata

## Description

## USE PEP 639-compliant license metadata

This PR updates the project’s `pyproject.toml` to adopt [[PEP 639](https://peps.python.org/pep-0639/)](https://peps.python.org/pep-0639/) license specification, as recommended by [[Python Packaging Authority](https://packaging.python.org/en/latest/guides/writing-pyproject-toml/#license)]. 

### Changes:

* Changed deprecated `license = {file = "LICENSE"}` table syntax to `license = "MIT"` as a valid SPDX expression (string).
* Added `license-files = ["LICENSE"]` to explicitly include the license file.
* Removed outdated `License :: OSI Approved :: MIT License` classifier, which is now discouraged in favor of SPDX.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `85c015432291`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.