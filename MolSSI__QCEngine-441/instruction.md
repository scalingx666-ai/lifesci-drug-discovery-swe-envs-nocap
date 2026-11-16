# Issue

**Title:** Add a harness for MACE-OFF23 and local MACE models

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This PR adds a new harness for ML models based on the MACE architecture, supporting local models and three general organic force field published models (MACE-OFF23) which can be found [here](https://github.com/ACEsuit/mace-off). More information about the performance can be found [here](https://doi.org/10.48550/arXiv.2312.15211).

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
Add new harness for MACE ML models supporting local and the general MACE-OFF23 models.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7cad296f0285`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.