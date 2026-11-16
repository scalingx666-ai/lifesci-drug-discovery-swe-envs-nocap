# Issue

**Title:** Minor issues involving >1 core per MPI rank

## Description

## Description
Fixes bugs with how the total number of ranks and memory size for NWChem are determined when there is more than one core per MPI rank

## Changelog description
Minor bug fixes for NWChem when more than core per MPI rank is used

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7a145949b18a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.