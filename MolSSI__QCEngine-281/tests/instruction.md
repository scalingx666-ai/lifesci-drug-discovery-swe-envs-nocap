# Issue

**Title:** Harness for using NWChem's relaxation engine

## Description

## Description
Adds a harness that uses NWChem's built-in geometry optimizer

My hope is that this will be faster on HPC when my time to launch an NWChem run is significant.

## Changelog description
Adds a harness for geometry optimization with NWChem

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5a70317eca18`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.