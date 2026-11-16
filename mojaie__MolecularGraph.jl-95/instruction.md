# Issue

**Title:** Support sdf and mol generation from inchi string

## Description

Currently, only molecule generation is only supported from sdf formats or smiles.
This PR adds sdf and molecule generation from inchi strings.
The current libinchi version v1.05 does not support  generation of chiral sdf files. If we would update to libv1.06 we would also parse chiral inchi strings.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5ed6a939eb8c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.