# Issue

**Title:** Added TeraChemFrontEndHarness. Refactored TeraChemPBSHarness share co…

## Description

…de effectively with TeraChemFrontEndHarness.

<!-- Thank you for your contribution! -->

## Description
TeraChem's server mode has been extended to support file input/output alongside its protocol buffer interface. This allows more expressive put/get of large files to/from TeraChem via its API. The `TeraChemFrontEndHarness` captures this new functionality and will allow TeraChem to meet additional QCSchema specs (like returning stdout/stderror files, wavefunction data, etc.).

Since the `TeraChemFrontEndHarness` is an extension of the `TeraChemPBSHarness` the latter was refactored to more effectively reuse the shared code.

## Changelog description
Added `TeraChemFrontEndHarness`.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x ] Code base linted
- [ x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2dff41f632ad`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.