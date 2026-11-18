# Issue

**Title:** Initital working implementation / serial version

## Description

Serial version of ESP_GRID v0.1

Implemented in quick_oeproperties_module. 
Usage ESP_GRID (with user provided grid)

Prints coordinates and ESP (V_total) value to external file, in atomic units.
Default x,y,z, V
Can use x,y,z, V_nuc, V_elec, V_total

Limitations: 
- Scales poorly with grid size, when compared to ref. codes // not optimized. Need to look into loop structures and screening of integrals. 
- No MPI yet 
- No GPU yet 
- Code can use cleaning , will be doing that as we go.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `52127dbdc076`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.