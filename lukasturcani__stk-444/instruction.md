# Issue

**Title:** Add a Makefile for quickly running all checks

## Description

I've added a Makefile which can be used with `make check` so that
all the tests, and linting checks are performed in one go, rather
than the developer having to call them individually. This is purely
to help the local development workflow, it is not to be used with CI.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1160b35e0a0e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.