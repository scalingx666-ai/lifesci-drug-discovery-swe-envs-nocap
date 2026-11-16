# Issue

**Title:** pyenv which hint

## Description

<!-- Thank you for your contribution! -->

## Description
See  pyenv returns a path from `shutil.which` that, if its an unactivated conda env under pyenv management, isn't actually ready to run, so `qcelemental.which` is deceptive. Apart from checking err better on the qcengine side, this PR better handles the situation.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `poetry install; bash scripts/format.sh` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7443dab04992`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.