# Issue

**Title:** PEP 621

## Description

Move the metadata and as much setuptools configuration as possible
to pyproject.toml.

This reduces reliance on setup.cfg, and maximally generalizes
the build system configuration as supported by setuptools 61.0.

TODO:
* update cookiecutter version
* update documentation

Per discussion at #149, it seems appropriate to wait at least a few months before finalizing and considering this PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `328892925a5c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.