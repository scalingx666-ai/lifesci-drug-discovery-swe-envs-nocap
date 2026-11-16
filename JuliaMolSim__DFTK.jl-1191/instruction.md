# Issue

**Title:** Don't require a psp to construct an OrbitalManifold

## Description

This makes the construction of a Hubbard term a bit nicer, especially in cases where the psp is not so easily accessed (e.g. when interfacing via AtomsBase or potentially AiiDA).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4a2c0230216f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.