# Issue

**Title:** Load Molecules Into Molecule Object

## Description

## Description

Load molecules directly into a `spyrmsd.molecule.Molecule` object and fix problem with single-model PDB file when loaded with `spyrmsd.io.loadall`/`spyrmsd.io.loadallmols`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e98104390168`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.