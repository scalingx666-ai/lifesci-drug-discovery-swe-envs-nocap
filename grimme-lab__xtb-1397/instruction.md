# Issue

**Title:** Activate solvation, electric fields, constraints and some properties with tblite

## Description

Activates the now fixed solvation with tblite. To be consistent with tblite, I added the non-parametrized versions of GBSA and ALPB. The electric field should have been working all along, but I also activated it through the CLI.

For constraints the required additional potentials were simply missing. I also added a summary output, which contains the constraint energy. 

Since we had no properties at all with tblite, I added the basic stuff via the tblite post-processing (additional properties will follow in further PRs).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3903350aa97d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.