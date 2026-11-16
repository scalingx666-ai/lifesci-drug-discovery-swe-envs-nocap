# Issue

**Title:** Linted files and updated import ordering so linter passes again

## Description

<!-- Thank you for your contribution! -->

## Description
local `make lint` and the GitHub workflow linting do not pass due to a few files not being correctly formatted or having imports incorrectly sorted. This PR simply lints/resorts imports so these checks pass again.

## Changelog description
Linted and ordered imports for a few `runner.py` files.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [ x] Code base linted
- [ x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2dff41f632ad`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.