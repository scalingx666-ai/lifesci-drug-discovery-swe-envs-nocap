# Issue

**Title:** Fix a double-free bug in GA conformer search found via Avogadro

## Description

Open Babel would routinely crash without output

## Summary by Sourcery

Bug Fixes:
- Resolve a double-free crash in GA conformer search by correctly transferring ownership of score and filter objects to OBConformerSearch.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0e94434fa75c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.