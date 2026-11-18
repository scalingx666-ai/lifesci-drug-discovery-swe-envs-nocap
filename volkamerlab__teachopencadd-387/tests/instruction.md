# Issue

**Title:** Docs CI: reactivate link checker

## Description

## Description
Reactivate linkchecks in the `Docs` CI workflow. This was deactivated for one deploy because the checks fail on self-referential links.

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `54125aaf8759`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.