# Issue

**Title:** Update Python in CI

## Description

## Description

* Update Python versions in CI. 
* Drop `macOS-14` runners
* Update `pre-commit` configuration
* Fix `mypy` complaints

Only the last four versions of Python are tested in CI.

## Checklist

- [ ] Tests
- [ ] Documentation
- [ ] Changelog

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `62dcd20b78c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.