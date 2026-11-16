# Issue

**Title:** SAPT(DFT)-D3/-D4 Empircal Dispersion Parameters

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
I have added optimized parameters for using two-body -d3 and -d4 dispersion with sapt(pbe0) and sapt(b3lyp). There are both intermolecular and supermolecular parameters with preference towards an intermolecular usage when computing interaction energies. Perhaps there should be a not of this somewhere to inform users of this difference.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
My goal is to include these parameters here in QCEngine ahead of a PR for psi4 that will make use of these parameters for SAPT(DFT)-D4(I) and SAPT(DFT)-D4(S). This would be consistent with how SAPT0-D3 and SAPT0-D4 in psi4 operates, leaving the parameters all in QCEngine.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8186b6585974`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.