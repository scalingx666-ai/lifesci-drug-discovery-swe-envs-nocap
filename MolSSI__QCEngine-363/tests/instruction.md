# Issue

**Title:** dir structure in execute and properties in Cfour

## Description

<!-- Thank you for your contribution! -->

## Description
One test fix and some miscellaneous little improvements. The change to `execute` is the only slightly daring one, I think.

## Changelog description
- [x] For Cfour harness, skip explicit `DERIV_LEVEL` setting when `driver = "properties"`. This is needed for DBOC, for example, where any user deriv level (at least 0 or 1) halts calc.
- [x] ~Fix `AtomicResult.native_files` empty test after qcel 0.25.~ Separated to #366 
- [x] Add Wiberg variable note David Dotson suggested in review.
- [x] In `qcengine.execute`, allow directory structure in files to be written to scratch/work directory. This is needed for some Psi4 tests where we copy in a plugin directory.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d73862338f38`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.