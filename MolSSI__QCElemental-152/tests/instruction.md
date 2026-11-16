# Issue

**Title:** Molecule: read and write xyz+, implement kwargs for from_data/file

## Description

## Description
This PR fixes xyz+ reading and writing for Molecules and makes kwargs work in from_data and from_file. This is motivated by difficulties encountered when specifying charge and spin states.

## Status
- [ ] Changelog updated
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `be1b2e7400ae`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.