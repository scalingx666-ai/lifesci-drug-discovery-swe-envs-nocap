# Issue

**Title:** poetry to setuptools; min py38

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
- [x] After all-but-py37 builds spontaneously broke in the last few days, it's easier to move the build backend back in line with other QCA projects (QCFractal and QCManyBody) rather than find the issue with poetry's solve-all-at-once and highly-version-specified format.
- [x] This should hit most poetry uses and examples. I've already confirmed that new builds on `master` didn't break, so fine targeting this to `next2024`.
- [x] Dialed back the pydantic versions for docs build. There's some errors with latest pydantic, so that pin needs investigating and releasing.
- [x] Also bump the min python to 3.8+. Even that is end-of-life but QCEngine test lanes still use it.
- There will likely be refinements and corrections to this switchover, but this is a largely working start.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `poetry install; bash scripts/format.sh` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `44556c095237`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.