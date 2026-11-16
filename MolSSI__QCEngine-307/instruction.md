# Issue

**Title:** Error correction for NWChem computations that fail to converge

## Description

<!-- Thank you for your contribution! -->

## Description
Adds a simple error corrector for NWChem: Increase the number of iterations if it fails to converge

## Changelog description
Automatically increase the number of iterations when NWChem fails to converge

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cf5fdc50ea9d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.