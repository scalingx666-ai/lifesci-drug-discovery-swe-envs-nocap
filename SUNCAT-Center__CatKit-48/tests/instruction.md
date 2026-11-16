# Issue

**Title:** Small enhancements for `cathub organize`

## Description

- default file format for `cathub organize` has changed from `traj` to `json`. Rationale: the stability issues of the `traj` format for long term storage do not seem to justify the possible benefits of slightly reduced fill sizes for atomic structures. Both can be read/written using `ase.io`
- two bugfixes in `cathub organize` after getting user feedback
- two more test cases

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6c7c6ab4c2ed`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.