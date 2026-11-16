# Issue

**Title:** Add in restart capability to NWChem

## Description

## Description
Adds the ability for NWChem computations to be restartable.

If NWChem terminates due to walltime it leaves the scratch directory. This commit gives each computation a repeatably-named output directory, so that the QCEngine will restart from that directory if it still exists.

## Changelog description
NWChem can restart if QCEngine is killed

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc438bb74971`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.