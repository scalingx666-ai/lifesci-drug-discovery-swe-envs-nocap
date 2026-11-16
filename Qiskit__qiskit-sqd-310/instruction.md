# Issue

**Title:** Add official support for Python 3.14

## Description

## Summary

Adds official support for Python 3.14, following the same pattern as the recently merged Python 3.13 PR (#309).

## Changes

- **`pyproject.toml`**: add the `Programming Language :: Python :: 3.14` classifier.
- **`tox.ini`**: extend the `envlist` and the notebook test environment factors to include `py314`.
- **`.github/workflows/test_latest_versions.yml`**: add `3.14` to the matrix and bump the macOS job to `3.14`.
- **`.github/workflows/test_development_versions.yml`**: bump the newest matrix entry from `3.13` to `3.14`.
- **`releasenotes/notes/add-py313-*.yaml`**: updated the existing 3.13 release note to also announce 3.14, rather than adding a separate note.

`requires-python` already reads `>=3.10`, so no change is needed there.

## Notes for reviewers

As with the 3.13 PR, the macOS and development-version newest-Python jobs were bumped to `3.14` to keep testing on the newest supported version.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `358ecf08ab47`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.