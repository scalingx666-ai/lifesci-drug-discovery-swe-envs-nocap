# Issue

**Title:** Add official support for Python 3.13

## Description

## Summary

Adds official support for Python 3.13, following the same pattern used when earlier Python versions were added/dropped (e.g. #256, #83) and matching the configuration of sibling addons such as `qiskit-addon-utils` (which already supports 3.13).

## Changes

- **`pyproject.toml`**: add the `Programming Language :: Python :: 3.13` classifier.
- **`tox.ini`**: extend the `envlist` and the notebook test environment factors to include `py313`.
- **`.github/workflows/test_latest_versions.yml`**: add `3.13` to the matrix and bump the macOS job to `3.13`.
- **`.github/workflows/test_development_versions.yml`**: add `3.13` to the matrix (replacing the previous newest `3.12`).
- **`releasenotes/notes/add-py313-*.yaml`**: release note announcing the new support.

`requires-python` already reads `>=3.10`, so no change is needed there.

## Notes for reviewers

The macOS and development-version newest-Python jobs were bumped from 3.12 → 3.13 to keep testing on the newest supported version, consistent with `qiskit-addon-utils`. Let me know if you'd prefer to keep an explicit 3.12 macOS/dev entry instead.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1f402c3caf98`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.