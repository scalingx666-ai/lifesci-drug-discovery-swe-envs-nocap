# Issue

**Title:** MPI task support

## Description

## Description
Adds ability for QCEngine to invoke node-parallel tasks.

Implementing this required adding more information to the task configuration object and some utility functions for making an MPI configuration given a task configuration.

I also implemented support for NWChem, which seems to be working. 🤞 

## Todos
- [x] Add ability to get the CPU info of compute nodes

## Questions

## Status
- [ ] Changelog updated
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f5fba27bab7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.