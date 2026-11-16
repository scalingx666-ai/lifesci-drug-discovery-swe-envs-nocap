# Issue

**Title:** Improve usability

## Description

- [x] Faster rotation of molecules
- [x] Add an `Allocation` value
- [x] Define a custom setter for `Config` attributes 
- [x] Improve plotting aesthetics
- [x] Rebase

~Change reactant_to_product -> .to_product()~
Will break backwards compatibility, so best to change in v.1.2

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee67336a7e2b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.