# Issue

**Title:** Add converters between Schrodinger MAE and QCSchema Molecule

## Description

<!-- Thank you for your contribution! -->

## Description
Uses schrodinger.structure API to read and write structure objects to convert to/from QCSchema Molecule. 

Mae files can contain essentially arbitrary metadata about a molecule and its atoms, including calculation results. For this converter to Molecule, we just focus on porting structural properties (charge, multiplicity, bond orders), avoiding dumping a bunch of not necessarily structural information in `extras`

Dummies and counterpoise/ghost atoms are accounted for. Maestro limits bond orders to just {0,1,2,3} (aromaticity is inferred from bond patterns); by default we block lossy conversion of non-integer bond orders from Molecule, but we offer a permissive mode in the converter to just round to the nearest valid bond order.

The portions of the Python API used for interconversion are available even if the user has just installed Maestro (which if offered free to academics) rather than the whole Schrodinger Suite.

## Changelog description
Add converters between Schrodinger MAE and QCSchema Molecule

## Status
<!-- Please `bash scripts/format.sh` in the base folder or use pre-commit. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `46034a0587e2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.