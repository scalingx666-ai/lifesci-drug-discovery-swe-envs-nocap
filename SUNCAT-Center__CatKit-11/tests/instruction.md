# Issue

**Title:** Added catkit.api to setup.py for installation

## Description

Setuptools wants you to list every directory with python files that you want to include in the installation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8224fddd8c2f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.