# Issue

**Title:** Generalize Some Radial Transformations

## Description

Generalize radial transformations specific to HortonGrids/UniformInteger Grids. Specific to issue #143. 

The following grids were generalized to work over any grid:
- ExpRTransform
- LinearInfiniteRTransform
- PowerRTransform

The following grid wasn't generalized because it requires some assumptions on the parameters and is very heavy parameter fiddling
- HyperbolicRTransform.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3edfb576ef44`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.