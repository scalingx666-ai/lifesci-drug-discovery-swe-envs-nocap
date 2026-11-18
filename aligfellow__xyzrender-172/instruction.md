# Issue

**Title:** Chiral hydrogens viewed by default

## Description

Hydrogens attached to R/S stereocenters are now shown by default, including when `--no-hy` is passed. This uses
xyzgraph's built-in `assign_rs()` detection to identify
stereocenters whose hydrogens would previously have been hidden.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5fe916c647cd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.