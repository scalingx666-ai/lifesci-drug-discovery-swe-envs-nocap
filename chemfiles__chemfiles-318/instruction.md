# Issue

**Title:** feat: NetCDF scale factor

## Description

Found some old script that uses `scale_factor` in NetCDF extensively. This PR implements scaling of cell lengths, angles, coordinates and velocities by `scale_factor`.
.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b155bfbddfc8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.