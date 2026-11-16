# Issue

**Title:** Drop support for Python 2.7

## Description

Python 2.7 was sunsetted 2.5 years ago. It's becoming annoying to support it, and from PyPI and conda download stats, almost none of our users are still using Python 2.7. This PR officially drops Python 2.7 support.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c110986b3a9e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.