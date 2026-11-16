# Issue

**Title:** Serenity: Molecular Orbital Information

## Description

Serenity keeps MO information in binary .h5 files that can be found in a directory with the given molecular system name. My implementation assumes that the output file is still where it was left by Serenity, so that the molecule directory can be found relative to that path.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e4150f0391ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.