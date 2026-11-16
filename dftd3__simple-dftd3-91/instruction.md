# Issue

**Title:** New D3(BJ) parametrizations

## Description

The values are taken from:
1) https://www.rsc.org/suppdata/c7/cp/c7cp04913g/c7cp04913g1.pdf  (PW91)
2) https://doi.org/10.1039/C6CP00688D (dRPA75)
3) https://pubs.acs.org/doi/10.1021/acs.jpca.1c01295 (SCS-dRPA75, optSCS-dRPA75, and DSD-...)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1f4e4591f4d7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.