# Issue

**Title:** Bugfix/ python3.12 compatibility issue

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [x] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [x] Have you written new tests for your core changes, as applicable?
- [ ] Have you successfully ran tests with your changes locally?

**Description**
This PR aims to fix the `Python 3.12` compatibility issue with Bentoml. Implementation to be done within the fetch at the beginning (regardless of whether it's bentoml, or fastapi), just to be safe.
Bug: The issue stems from `pkg_resources` incompatibility with `Python 3.12` due to the removal of `pkgutil.ImpImporter`. 
`Python 3.12` removed `pkgutil.ImpImporter` and also stopped pre-installing `setuptools` in` venv` environments.` setuptools` is no longer automatically installed when you create a fresh environment with `Python 3.12`, specifically if you are using `venv` (the standard library's virtual environment tool). To access` setuptools`, you must explicitly install it after activating the environment
However, if you are using `Conda` to create the environment, `setuptools` might still be pre-installed. This is because  `Conda `handles package and environment dependencies differently and aims to provide a more complete setup by default.

**Changes to be made**

1. add a check for the python version in the code. 
2. if a user is operating from a 3.12 environment, try to import setuptools
3. if there's an import error, install setuptools (while also logging this on the CLI)
4. Add READme

**Status**

1. Python Version Check:

  - Added a check for `Python version >= 3.12` using `sys.version_info`.

2. Setuptools Import and Installation:

- Tries to import `setuptools` using `importlib.import_module`.
- If `ImportError` occurs, installs `setuptools` using `run_command("pip install setuptools")` and logs the process.

3. Logging:

- Detailed logging for successful installation, detection of `setuptools`, and error handling.

4. Documented the fix for README

Is this pull request related to any open issue? If yes, replace issueID below with the issue ID

Fix #1379

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c5d1ee09d414`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.