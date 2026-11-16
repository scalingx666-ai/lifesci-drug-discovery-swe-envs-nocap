# Issue

**Title:** Dimension deprecation: reorder_qt

## Description

## Description
Breaks up #3351

Part of a larger effort to deprecate those pesky Dimension operators. Changes function signatures of `reorder_qt` and `reorder_qt_uhf` from `int*` to `Dimension const&`.

## User API & Changelog headlines
- Minor API: `reorder_qt[_uhf]` function signatures changed.

## Dev notes & details
- See description.

## Checklist
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d8eac07ac32`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.