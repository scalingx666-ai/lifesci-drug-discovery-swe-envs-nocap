# Issue

**Title:** Ensure that molecule orientation remains fixed for MDI

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->

This is a simple bug fix to ensure that molecules remain fixed during MDI calculations.  Otherwise, there is a possibility that certain codes may rotate the molecule, which renders quantities such as forces unusable by external drivers.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

Ensure that molecule orientation remains fixed for MDI.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cbec059bb521`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.