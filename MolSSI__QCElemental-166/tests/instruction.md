# Issue

**Title:** Molecule: Updates nglview-sdf

## Description

Updates the `nglview-sdf` string method to use `nglviews` internal float text widths. This removes the need for a center of mass movement which may not be desired.



## Status
- [ ] Changelog updated
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `16b2de82eb60`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.