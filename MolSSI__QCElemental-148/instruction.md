# Issue

**Title:** NGLView Integration

## Description

## Description
Swaps out py3DMol for NGLView. The primary benefit here is that we have direct widget integration so that we can do fun things showing both a Plotly plot and a Molecule at the same time.

Other features:
 - New technology to guess the molecules connectivity based off vanderwaals radii.
 - Quasi SDF file format, really just good enough for visualization. @jwags

## Status
- [ ] Changelog updated
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `29fda275ba29`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.