# Issue

**Title:** Set band-edge marker size in style file

## Description

Raised in #192 ; how can users adjust the size of VBM/CBM markers? This is currently hard-coded but does not need to be.

The CBM/VBM edge markers are plotted with `scatter`, which has a default marker size of s = rcParams['lines.markersize'] ** 2.

Our hard-coded `s=100` is rather chunky, so by replacing this with an equivalent value in the style file we allow users to customize it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a4e93f9bd177`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.