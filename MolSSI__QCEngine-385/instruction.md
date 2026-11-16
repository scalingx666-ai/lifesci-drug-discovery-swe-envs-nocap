# Issue

**Title:** adapt s-dftd3 harness for psi4

## Description

<!-- Thank you for your contribution! -->

## Description
- [x] Changes the dispersion coefficient resources for D3 variants so that there's a `2b` set (e.g., `d3bj2b`) that is pure 2-body and doesn't accept `s9` (effectively fixed at 0.0) and a `atm` set (e.g., `d3zeroatm`) that does accept `s9` (by default 1.0 but user-variable).
- [x] Previous aliases are mapped to `2b`, so classic dftd3 doesn't change. s-dftd3 tests remain unchanged but if keyword `apply_qcengine_aliases` is True (psi4 does this), the level hints are interpreted into standard s-dftd3 input.
- [x] @awvwgk, this is my attempt at transitioning from dftd3 -> s-dftd3 while (1) not breaking Psi4's d3 behavior, (2) not locking Psi4's d3 into s9=0.0, (3) not requiring full parameter spec just to tweak s9, and (4) not overwriting your reasonable and released defaults and behavior for the s-dftd3 interface. It's not as clean as I would like, but I think it's workable. Any comments, concerns, or questions?
- [x] fixes classic dftd3 harness pairwise analysis array to be scaled like s-dftd3. see changelog for details.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `992e67f51983`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.