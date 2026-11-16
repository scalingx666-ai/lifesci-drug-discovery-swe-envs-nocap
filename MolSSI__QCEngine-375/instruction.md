# Issue

**Title:** stdsuite testing remp2, oo, dfcc

## Description

<!-- Thank you for your contribution! -->

## Description
This pairs with  It doesn't affect QCEngine's general purpose, so I'll plan to mint a v0.24.1 with this when the Psi4 use is finalized.

Adds ref values for df ccsd, ccsd(t), a-ccsd(t), for orbital-optimized mp2, mp2.5, mp3, ccd, ccd(t), a-ccd(t), and for remp2 and oremp2. Existing reference values computed with Psi4's dfocc and occ modules have been updated now that it can converge tighter.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0d8330408f48`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.