# Issue

**Title:** Add an SCF/EFP reference implementation.

## Description

## Description
Shows how to use libefp in an SCF/EFP sp

## What are your new additions? Please provide a brief list.
* **New Features**
  - [x] SCF/EFP sp

## Any questions for the community?
- [x] I'll have to rework the testing structure a bit and move to pytest to handle the very specific versions this requires cleanly. This will almost certainly break current testing infrastructure b/c needs recent psi4 and unreleased pylibefp.

## Status
- [x] Click when ready for review-and-merge. ~Review, sure. Merge, no.~

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6747b7ea0f13`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.