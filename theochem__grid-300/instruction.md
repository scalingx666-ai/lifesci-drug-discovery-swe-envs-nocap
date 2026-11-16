# Issue

**Title:** Phase out tox

## Description

Grid was using `pyproject.toml` and `tox.ini` as duplicated sources of truth for package configuration. 
This PR sets  `pyproject.toml` as the only source of truth.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c025306ad288`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.