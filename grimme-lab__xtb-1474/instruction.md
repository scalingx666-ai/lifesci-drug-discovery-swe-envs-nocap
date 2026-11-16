# Issue

**Title:** Adapt Fermi smearing from tblite

## Description

Performs the same fixes for the Fermi smearing as in tblite (). This includes:

- start from Aufbau occupation
- clip to exactly occupied or exactly empty orbitals with large exponents. 
- use a stable exponential function to evaluate the occupation and its derivative. 
- tighter thresholds for convergence of the Fermi iterations
- testing both internally and directly w.r.t. tblite

There are some small differences in the edge cases with zero temperature or zero electrons where xtb returns the HOMO/LUMO midpoint or the lowest orbital energy instead of zero for tblite. 

This prepares the long-term switch to using tblite for all Hamiltonians by fully aligning the xtb and tblite SCF results.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3a46d03d735b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.