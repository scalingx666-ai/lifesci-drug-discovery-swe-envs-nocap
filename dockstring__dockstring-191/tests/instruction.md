# Issue

**Title:** Update GitHub Actions files

## Description

This pull request updates the GitHub Actions workflows to use newer versions of actions and improves Python environment setup and caching for linting, testing, and publishing. The changes modernize the workflows, ensure compatibility with Python 3.11, and streamline package management and build steps.

**Workflow modernization and dependency management:**

* Updated all workflows (`lint.yml`, `run-tests.yml`, `publish-to-test-pypi.yml`) to use the latest versions of GitHub Actions (`actions/checkout@v4`, `actions/cache@v4`, `setup-python@v5`, `setup-miniconda@v3`) for improved reliability and features. [[1]](diffhunk://#diff-107e910e9f2ebfb9a741fa10b2aa7100cc1fc4f5f3aca2dfe78b905cbd73c0d2L6-R27) [[2]](diffhunk://#diff-7314d0ebbd2e9537ae4889316745b4fd2fa43cb86275c9caae18a86ba228b642L26-R38)
* Upgraded Python version to 3.11 across workflows and added pip caching to speed up dependency installation and improve consistency. [[1]](diffhunk://#diff-107e910e9f2ebfb9a741fa10b2aa7100cc1fc4f5f3aca2dfe78b905cbd73c0d2L6-R27) [[2]](diffhunk://#diff-589b92445dc6f8ac68673fd9b852b4e366ab69127e791b0fd0c6b43a7a607ac2R19-R40)
* Improved pip installation steps by adding explicit upgrades and using unified commands (`python -m pip install ...`) for consistency. [[1]](diffhunk://#diff-107e910e9f2ebfb9a741fa10b2aa7100cc1fc4f5f3aca2dfe78b905cbd73c0d2L6-R27) [[2]](diffhunk://#diff-589b92445dc6f8ac68673fd9b852b4e366ab69127e791b0fd0c6b43a7a607ac2R19-R40)

**Build and test process improvements:**

* Changed build and test commands to use `python` instead of `python3` for consistency and future compatibility. [[1]](diffhunk://#diff-589b92445dc6f8ac68673fd9b852b4e366ab69127e791b0fd0c6b43a7a607ac2R19-R40) [[2]](diffhunk://#diff-7314d0ebbd2e9537ae4889316745b4fd2fa43cb86275c9caae18a86ba228b642L56-R55)
* Enhanced pre-commit linting by showing diffs on failure for easier debugging.

**Minor workflow formatting:**

* Updated job names for clarity and removed unnecessary formatting in `publish-to-test-pypi.yml`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79f705912a2d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.