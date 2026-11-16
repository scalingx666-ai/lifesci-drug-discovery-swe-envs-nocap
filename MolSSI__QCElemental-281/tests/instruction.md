# Issue

**Title:** Allow multiple input molecules for torsiondrives

## Description

## Description
This PR syncs up the QCElemental and QCFractal torsion drive inputs to accept multiple input molecules, which will also allow QCEngine to run torsiondrives using multiple inputs once I have a PR there.

## Changelog description
Allow the `TorsionDriveInput` `initial_molecule` field to be a list of at least one `Molecule`.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a5885ee4421b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.