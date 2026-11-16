# Issue

**Title:** Fix floating-point bug in `compute_angle`

## Description

<!-- Thank you for your contribution! -->

## Description
Fixes the bug described in #324 by ensuring that the calculated cosine has a valid value between [-1, 1].

## Changelog description
Fixed a bug causing `qcel.util.measure_coordinates` to return `nan` values.

## Status
<!-- Please `poetry install; bash scripts/format.sh` in the base folder. -->
- [ ] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `24c6fb96ff6b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.