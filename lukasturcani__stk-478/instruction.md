# Issue

**Title:** Implement initialization with pathlib.Path

## Description

``xyz``, ``pdb``, and ``mdl_mol`` can now be initialized using pathlib.Paths.

Updated the type hints to allow pathlibs and imported pathlib

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67c00dec2bd1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.