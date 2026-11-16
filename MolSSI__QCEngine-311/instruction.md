# Issue

**Title:** store computational module (e.g., tce) in provenance

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Next installment in #310 

## Changelog description
- [x] CFOUR, GAMESS, NWChem harnesses learned to notice which internal module performs a calc (e.g., tce/cc for NWChem) and to store it in `atres.provenance.module`.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `675c52679df5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.