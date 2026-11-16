# Issue

**Title:** standard suite for HF, MP2.5, MP3, LCCD grad

## Description

<!-- Thank you for your contribution! -->

## Description
Add reference data for HF gradients, MP3 energies & gradients, and LCCD gradients. Expand contract machinery for HF, MP2.5, MP3, LCCD. Harvest MP3 from Cfour

Also converted the psi4 (non-nightly) conda-env into a "minimum" testing environment.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `236156f3101d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.