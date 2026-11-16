# Issue

**Title:** qchem mol

## Description

## Description
Qchem

## Todos
  - [x] `molparse.to_string` Q-Chem dtype developed. 
  - [x] Psi4 dtype now includes label and doesn't have extraneous info for single fragment systems.

## Questions
- [ ] Note that qchem handling of `fix_*` via `no_reorient`, `sym_ignore`, or more likely a tangle, is unclear, and needs practical testing

## Status
- [x] Changelog updated
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3447ddcbff86`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.