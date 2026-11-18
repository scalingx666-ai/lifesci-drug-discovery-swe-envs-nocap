# Issue

**Title:** Small fixes in T021

## Description

This PR fixes small things in T021:

- ChEMBL25 is used in the notebook. In the theory, v17 was mentioned. This has been updated and numbers are taken from here: https://ftp.ebi.ac.uk/pub/databases/chembl/ChEMBLdb/releases/chembl_25/chembl_25_release_notes.txt
- SMILES and atoms were sometimes in quotes, sometimes in code style. Now all is in code style.
- Quotes were not consistent (single, forward double, etc.), now all consistent to " .
- Numbers were not in math mode.
- Remove extra long cell output.
- Remove unused library reference (timeit).
- Remove the bracket when mention a function in markdown.
- Minor formulation edits.

_Note_:
I still think that we should remove the suppl. material in this notebook.


### Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e36208ed3207`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.