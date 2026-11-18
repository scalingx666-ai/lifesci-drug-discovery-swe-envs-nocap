# Issue

**Title:** Bug fixes

## Description

Fix bug where nci was not passed correctly to gif, MO gif did not respect orientation, gif-ts and gif-rot did not respect interactive rotation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `136c81476673`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.