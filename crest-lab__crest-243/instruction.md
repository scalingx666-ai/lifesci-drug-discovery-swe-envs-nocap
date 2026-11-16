# Issue

**Title:** Update QCG input file processing

## Description

The processing of the solute and solvent file for QCG was updated and moved to _solvtool.f90_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `035c4e044e4e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.