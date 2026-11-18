# Issue

**Title:** Preserve NCIs across ensemble conformers

## Description

This is a bit niche, but came across this while working on implementing NCI type specification. This PR preserves per-conformer NCI interactions when rendering ensembles, including centroid-based interactions in static and GIF output. This keeps interaction rendering accurate when geometry differs between conformers.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4fc03ddbb85b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.