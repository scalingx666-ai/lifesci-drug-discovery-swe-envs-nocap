# Issue

**Title:** Remove unused util/autodoc module

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Originally, there were some custom functionality for generating docs from pydantic. We've since moved to autodoc-pydantic.

This had been kept for the old qcfractal versions, but that was several years ago. I do not see this stuff being used anywhere in the qcelemental codebase anymore.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
Remove unused pydantic autodoc classes and functions (`util/autodocs.py` module)

## Status
<!-- Please `poetry install; bash scripts/format.sh` in the base folder. -->
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4e3b97565c9d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.