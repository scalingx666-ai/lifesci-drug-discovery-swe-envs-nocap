# Issue

**Title:** Reduce number of SQLAlchemySocket instances created on startup

## Description

## Description
Small improvement to how QCFractal servers start up.

This change reducing the times an `SQLAlchemySocket` object need to be created (which can be somewhat expensive). Very minor, just something I noticed while benchmarking some other areas.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `05570783c57a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.