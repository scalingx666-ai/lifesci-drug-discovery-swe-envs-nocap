# Issue

**Title:** chore: bump version to v4.0.2 and fix archive title mismatch

## Description

## Summary
- Bumps the package version to v4.0.2 for the JOSS-reviewed release (openjournals/joss-reviews#11015)
- Fixes `CITATION.cff` and `.zenodo.json` title, which carried the repo's old generic tagline instead of the JOSS paper title ("SMACT v4: Enhanced Screening and Prediction Tools for Computational Materials Design")
- The v4.0.1 Zenodo archive was created from the commit predating #673, so it's still missing Masahiro Negishi and most ORCIDs. This retag lets a fresh Zenodo deposit archive the fully corrected metadata (title + all 14 authors + ORCIDs), verified against joss/paper.md with zero mismatches.

## Test plan
- [x] `uv lock` regenerated to reflect the new project version
- [x] Programmatically diffed .zenodo.json/CITATION.cff author names + ORCIDs against joss/paper.md: 0 mismatches
- [x] Confirmed title now matches joss/paper.md exactly in both files

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **Documentation**
  * Updated the software title and citation metadata to reflect SMACT v4.
  * Updated the published version to 4.0.2.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ab3143df43a9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.