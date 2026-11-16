# Issue

**Title:** test CI

## Description

<!-- Thank you for your contribution! -->

## Description
Heal CI caused by (1) Libint2 making it to c-f proper (not conda-forge/label/libint_dev), (2) psi4 and Libint2 AM expectations out of sync b/c different channels or different builds, (3) expanded Hess capacities raising a different error msg.
## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7cad296f0285`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.