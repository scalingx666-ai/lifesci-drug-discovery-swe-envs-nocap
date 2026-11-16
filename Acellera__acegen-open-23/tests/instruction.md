# Issue

**Title:** Less log directory inception when using MolScore

## Description

MolScore logs are now collapsed into acegen log directory.

Needs latest version of MolScore on pip with `pip install molscore --upgrade`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8f40c125cdba`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.