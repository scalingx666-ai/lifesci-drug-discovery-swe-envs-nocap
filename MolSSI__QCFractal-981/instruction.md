# Issue

**Title:** Vendor in some models from qcelemental

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

This is part of a migration to pydantic v2.

Because of the long-lived nature of the QCFractal database, we can be a bit sensitive to input parameters which are used in de-duplication. So given the changes coming towards QCElemental/schema (version 2, required for pydantic v2), we should copy some of the models we directly import from QCElemental.

These are small models - mostly protocols and provenance. This allows us to be a little more flexible with legacy data while QCElemental goes through the changes.

I have no plans for vendoring the big models, though (`Molecule` and `WavefunctionProperties`). Most other imports are for validating/creating those models directly (ie, creating `AtomicResult` from our SinglepointRecord) so should stay.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c412f9b30933`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.