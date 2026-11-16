# Issue

**Title:** fix: unify post-filter results and retry invalid candidate rankings

## Description

- Unify Post-filter and Design result layouts.
- Make sort menus scrollable and include all available metrics.
- Restore missing contact and loss evidence in Post-filter results.
- Retry invalid PostFilter rankings up to 3 total attempts with corrective feedback.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6510a6f6f4a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.