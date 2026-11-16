# Issue

**Title:** Expose FreeSASA's test-point and slice counts in SASAOpts

## Description

<!--
Thanks for contributing a pull request!

Please review the contributing guide before submitting:
https://github.com/rdkit/rdkit/blob/master/Docs/Book/GettingStartedWithContributing.md
-->
#### Reference Issue
<!-- Example:  -->
None.

#### What does this implement/fix? Explain your changes.
`calcSASA` builds its FreeSASA parameters from `freesasa_default_parameters` and sets only the algorithm and the probe radius. That leaves the resolution fixed at FreeSASA's defaults: 100 test points per atom for Shrake-Rupley and 20 slices per atom for Lee-Richards.

This PR adds two fields to `SASAOpts`:

- `shrakeRupleyNumPoints` (default 100)
- `leeRichardsNumSlices` (default 20)

Both default to FreeSASA's own constants (`FREESASA_DEF_SR_N`, `FREESASA_DEF_LR_N`), so existing results don't change. They're exposed in both the boost.python and nanobind wrappers, with docstrings.

A value of zero or below raises a `ValueErrorException`. FreeSASA rejects such a value, and `calcSASA` would otherwise silently return 0.0.

Tests:
- `testResolution()` in `testFreeSASA.cpp` and `test_resolution` in `Wrap/testFreeSASA.py`. They check the defaults, the area of 1d3z at 1000 points and at 40 slices, and the error for 0.
- The expected values at 1000 points and 40 slices were computed independently with the standalone `freesasa` Python package. It reproduces the existing 1d3z references exactly at the default settings, and RDKit's build reproduces the new values.

#### Any other comments?
Purpose: we'd like to use this option directly in [scikit-fingerprints](https://github.com/MLCIL/scikit-fingerprints), where we compute Mordred's CPSA descriptors on top of `CalcSASA`. Mordred uses a Shrake-Rupley mesh of about 2,500 points per atom, so FreeSASA's fixed 100 points can't match it closely. More generally, the resolution is a speed/accuracy trade-off that should be up to the caller, so this should be useful to anyone else who uses `CalcSASA`. Exposing the slice count for Lee-Richards seemed natural at the same time.

Tested locally on macOS arm64 (Apple clang, Boost 1.92):
- Full `ctest` suite with the default build options plus `RDK_BUILD_FREESASA_SUPPORT=ON` (boost.python wrappers, Python 3.15): all 281 tests pass.
- `testFreeSASALib` and `testFreeSASA.py` also pass with the nanobind wrappers (Python 3.13). `leaks --atExit` reports 0 leaks for `testFreeSASALib`.

AI disclosure: I used Claude Code (Claude Opus 5.5) to write the change and the tests, to build RDKit and run the tests, and to cross-check the reference values. I reviewed the full diff myself before opening this PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2bbaa851cb56`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.