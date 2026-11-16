# Issue

**Title:** OpenMM harness update

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This PR refactors the OpenMM harness to use openmmforcefields system generator to allow the use of GAFF and openforcefields through qcengine. We also allow users to supply a mapped smiles  to help with accurate forcefield typing through the scheme extras.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
OpenMM harness now looks for cmiles information in the molecule extras field when typing. Also we allow for the use of gaff forcefields.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4b5843b059e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.