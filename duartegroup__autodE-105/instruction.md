# Issue

**Title:** Modify Calculation get_energy

## Description

by throwing a `CouldNotGetProperty` exception if an energy cannot be extracted from a completed calculation. Also adds a decorator for `Calculation` methods that require at least the name of the output filename to be set and hint that `run()` might have been forgotten to be called.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `421ceaad5d42`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.