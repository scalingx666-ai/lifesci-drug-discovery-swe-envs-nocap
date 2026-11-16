# Issue

**Title:** Bug fix in SAPT0(ROHF).

## Description

A simple fix in the code for the SAPT orbital energies. The old code sometimes picked energies from the wrong monomer in the open-shell case.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc0b51d9a052`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.