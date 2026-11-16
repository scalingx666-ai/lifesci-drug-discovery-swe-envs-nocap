# Issue

**Title:** Modernize packaging and CI

## Description

This PR switches from setuptools to flit for packaging and moves all setup code into a `pyproject.toml`. It also uses uv for faster installation and building. Conda installation is no longer the recommended method.

Due to dependency clashes, this PR drops support for Python 3.6-3.8, which cannot be installed and tested on CI.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `97aac93bc80f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.