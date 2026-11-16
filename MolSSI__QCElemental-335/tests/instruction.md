# Issue

**Title:** Use newer pint version for Python >=3.9

## Description

Pint  >= 0.10 fails for newer numpy versions, in particular >= 1.25.

This change bumps up the version requirements for Pint in cases where we are using newer numpy.

## Description
See  

## Changelog description
Use newer pint version for Python >=3.9

## Status
<!-- Please `poetry install; bash scripts/format.sh` in the base folder. -->
- [ ] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e942b810f168`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.