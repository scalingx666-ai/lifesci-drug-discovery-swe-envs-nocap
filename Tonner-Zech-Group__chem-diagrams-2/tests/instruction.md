# Issue

**Title:** Add py.typed marker for PEP 561 compliance

## Description

Adds an empty py.typed sentinel file so that type checkers (mypy, pyright, etc.) recognise chemdiagrams as a typed package and use its inline annotations when installed by downstream consumers.

Also registers the file as package data in pyproject.toml so that setuptools includes it in source and wheel distributions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bbf4236c8ce6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.