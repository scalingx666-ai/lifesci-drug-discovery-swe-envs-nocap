# Issue

**Title:** Allow NWChem to restart single-point computations

## Description

## Description
Allows restarts to work for single-point NWChem computations, adds tests for that functionality.

As written, the NWCHarness does not write the geometry to the input
file for restart calculations. This is great for Driver computations
because it prevents the computation from restarting from the initial
geometry. However, the geometry is required for single point calculations
(esp Hessian, Gradient) because we use the geometry to determine
how NWChem rotates the coordinate system so that we can adjust
any direction-dependant quantities back to the initial coordinate system.

This change is simple: I add a flag that is set by the "driver" computation
to tell the NWCHarness not to write the geometry for restarts.
For clarity, the NWCOptimizerHarness calls the NWChemHardness
to make input files

## Changelog description
Allow NWChem to restart single-point calculations

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `113d1e8b44a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.