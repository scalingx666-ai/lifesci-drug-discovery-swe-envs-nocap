# Issue

**Title:** chore: bump version to v4.0.1 for JOSS-reviewed release

## Description

## Summary
- Bumps the package version to v4.0.1, the release to be archived and tagged for the JOSS review (openjournals/joss-reviews#11015)
- Adds Masahiro Negishi to CITATION.cff (was missing) and fills in missing author ORCIDs so the archive metadata matches joss/paper.md

## Test plan
- [x] `uv lock` regenerated to reflect the new project version
- [x] Diff reviewed: only version bump and CITATION.cff author/ORCID fixes

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **Documentation**
  * Updated the project version to 4.0.1 and refreshed the release date.
  * Added author details, including ORCID identifiers and a new contributor.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7e40fc398636`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.