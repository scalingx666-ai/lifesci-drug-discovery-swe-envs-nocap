# Issue

**Title:** Reformat CHANGELOG

## Description

Changes made in this pull request:
- Cleanup `CHANGELOG.rst`.
- Change default `towncrier` formatting.
  - All references now link to the corresponding issue/pull request on GitHub.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `995f07a9c4ad`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.