# Issue

**Title:** Writes PRD code for chem_comp in CIF and PRDCC code for filename

## Description

PRDs are a little tricky with their filename. The CCD like files of PRDs have file name with PRDCC prefix, but inside the cif file the chem_comp has PRD prefix. While generating Component objects of PRDs, the component id was assigned from chem_comp_id inside CIF file (e.g. PRD prefix), but the output file name should have PRDCC prefix. Hence a new variable "outfile_prefix" is added to **process_single_components** function to deal with difference in PRDCC filename and PRD code in chem_comp

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c143527762f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.