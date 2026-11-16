# Issue

**Title:** Fix MMTF writer for non-biological systems

## Description

The code made a few assumption on what data was present in the frame, assumptions only matched by files containing biomolecular systems.

In particular, atoms are not guaranteed by chemfiles to be ordered inside residues, and not all atoms have associated residues.

@frodofine I would appreciate if you could give this a look! If you don't have time, that's fine, just let me know 😃

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `26174946b4b0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.