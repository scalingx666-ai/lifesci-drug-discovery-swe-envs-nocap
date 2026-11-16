# Issue

**Title:** Solvent aliases

## Description

Adds additional solvent aliases for various supported solvents.

`normalizeSolventName` now chooses a consistent name to use for a given solvent internally.
 
Addresses

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee064757917f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.