# Issue

**Title:** Remove versioneer

## Description

## Description

[versioneer]() is the likely cause of issues when automatically releasing to PyPI. The utility of the tool for a small package like `spyrmsd` is dubious, so I'm removing it here (it also reduces the maintenance burden).

Versions will need to be manually changed on release in `setup.py` and `spyrmsd/__init__.py`.

Close #87. Related to #54.

## Checklist

- [x] Tests
- [x] Changelog

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4c02adfde557`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.