# Issue

**Title:** Add checking for incompatible charge/mult

## Description

Adds a warning if the SMILES-calculated multiplicity doesn't match a non-default specified value and an exception if the charge doesn't match. Suggest using different behaviour between spin multiplicity and charge due to – I think – the former not being able to be specified in a SMILES string

### TODO:

- [ ] Add metal-complex test e.g. HS dn

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a4709992c18`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.