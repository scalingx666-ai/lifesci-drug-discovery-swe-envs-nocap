# Issue

**Title:** add more rich_escape calls

## Description

Addresses #117

Some text was not escaped properly for rich styling. This was exposed by a new version of textual.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eeff6c7c168d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.