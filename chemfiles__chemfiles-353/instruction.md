# Issue

**Title:** Implement Amber Restart Format

## Description

This enables chemfiles to read and write Amber Restart (.ncrst) files. Those files are pretty similar to Amber Trajectory files but use mostly doubles and contain only a single frame.
.

Additional:
- ~fix link to specs of .gro files~
- added check in LAMMPS Data tests for writing multiple frames ()
- read and write frame title property of Amber formats

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5db21ff30ab4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.