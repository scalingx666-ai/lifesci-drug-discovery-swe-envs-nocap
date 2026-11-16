# Issue

**Title:** Fix CI for Windows+Psi4, OpenMM

## Description

Updated psi4 version and commented out previous dependencies.

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
see changelog and edits.

Warning: the 3rd lane was sometimes passing / sometimes failing so beware of releasing changes after one pass. The psi4+Windows error look alot like the MKL version failures and include the telltale "tricky_ghost". qcengine.yaml seems the fix in both cases. The separation of pytest isn't the best sol'n. For the opt-disp-cf on Windows, I added rdkit back. It's been passing for 2 rounds of CI now, but it was nondeterministic before, too.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b3905b4362fb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.