# Issue

**Title:** further which patching for py312

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Continues #328 `which`+py312+windows handling, now preferring `.exe` over `.bat`. Tested at qcng.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `poetry install; bash scripts/format.sh` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b49b3181cf64`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.