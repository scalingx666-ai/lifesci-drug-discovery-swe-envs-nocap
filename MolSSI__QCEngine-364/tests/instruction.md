# Issue

**Title:** gradients with ghost atoms for cfour and nwchem

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->

## Changelog description
- [x] Expand the Xenon hack so that Cfour can run and harvest gradient jobs when molecule has ghost atoms.
- [x] Allow `geometry__autosym` keyword for NWChem. NWChem has a loose symmetrizer that can change the working geometry slightly more than QCEngine expects. Now that can be dialed back.
- [x] Test gradients with ghosts for Cfour (newly works), NWChem (newly matches), GAMESS (already skipped even for energies), and Psi4 (already worked).

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d73862338f38`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.