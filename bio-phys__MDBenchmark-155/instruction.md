# Issue

**Title:** Add Poetry

## Description

This PR adds [`poetry`](https://github.com/sdispater/poetry) as the _one_ dependency management tool for our project.

With `poetry` we can define all dependencies, locally install everything in isolated environments and also have the package deployed to PyPI.

PR Checklist
------------
- [x] Added changelog fragment in  `./changelog/`?
- [x] Add `CLASSIFIERS`.
- ~[ ] Make use of the `poetry version` function.~ Postponed for the future.
- [x] Update `DEVELOPER.rst` to include a how-to for `poetry`.
- [x] Move `setup.py`-things to `pyproject.toml`.
- ~[ ] Move `setup.cfg`-things to `pyproject.toml`.~ Postponed for the future.
- [x] Move `MANIFEST.in` to `pyproject.toml`.
- [x] Use `poetry` to run tests?
- [x] Make sure the documentation can be build by readthedocs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d153efa64c6c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.