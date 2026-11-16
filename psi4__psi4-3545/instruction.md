# Issue

**Title:** Xtpl v1110 mbis

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Warns/fixes callers of grid who expect the grid to be there, when it mightn't be b/c it's on the GPU. Allows MBIS to run with cuEST
- [x] There's an occasional misalignment btwn the memory query and the memory alloc for DF gradients. Confirmed bug that will be fixed in v0.2.2 . In the meantime, added some padding.
- [x] Considerable speedup of MBIS_CHARGES (15x on 109 atoms) . Squashed version of #3546

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e692c83d5cfc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.