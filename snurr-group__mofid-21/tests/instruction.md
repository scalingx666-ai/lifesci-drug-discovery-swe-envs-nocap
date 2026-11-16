# Issue

**Title:** Revisiting slurm scripts

## Description

Now that quest has [switched from moab to slurm](https://kb.northwestern.edu/page.php?id=89454), I needed to finish updating the moab workflows for HPC.  These scripts automate the process of extracting MOFid/MOFkey for the GA hMOF, ToBaCCo, and CoRE MOF databases, as well as running the validations.

@arosen93 could you check the modifications below?  I'd appreciate your experience with slurm.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79ea40474098`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.