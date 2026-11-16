# Issue

**Title:** Add MRChem harness

## Description

## Description
This adds a harness for [MRChem](mrchem.readthedocs.io), the multiresolution analysis DFT code developed at the university of Tromsø.

### TODOs
- [X] Proper handling of all drivers.
- [x] Test MPI invocation.
- [X] Proper translation between MRChem output schema and QCSchema output.
- [X] Translation from QCElemental molecule to MRChem ~~: MolSSI/QCElemental#238 pending~~

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
Add a harness for [MRChem](mrchem.readthedocs.io), the multiresolution analysis DFT code developed at the University of Tromsø.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [X] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ae97f3d4aa47`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.