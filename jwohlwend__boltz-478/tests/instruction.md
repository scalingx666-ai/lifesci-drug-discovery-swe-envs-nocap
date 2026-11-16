# Issue

**Title:** fix: redundant PoseBustersPotential bounds

## Description

- Makes a fix where I believe bond_buffer was intended rather than redundant angle_buffer.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8bf88eadf8c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.