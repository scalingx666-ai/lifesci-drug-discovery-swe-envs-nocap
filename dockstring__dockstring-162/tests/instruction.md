# Issue

**Title:** Fix package versioning issue.

## Description

After the last PR (#161) dockstring would be installed as `0.0.0` instead of using the version name from git tags.

I realized the issue was because I did not include an empty section called `[tool.setuptools_scm]` in `pyproject.toml`. This PR adds this, and also removes the outdated `_version.py` file which I forgot to remove in the last PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f5f57faa8628`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.