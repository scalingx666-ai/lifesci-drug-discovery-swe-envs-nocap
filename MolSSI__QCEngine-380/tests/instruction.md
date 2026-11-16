# Issue

**Title:** Enable geometry optimizations with MRChem

## Description

<!-- Thank you for your contribution! -->

## Description
I've modified the MRChem harness to accept input for the calculation of molecular gradients, which allows to use it with geometry optimization procedures.

## Changelog description
- MRChem can be used as engine for geometry optimizations.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `737ba765f7fd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.