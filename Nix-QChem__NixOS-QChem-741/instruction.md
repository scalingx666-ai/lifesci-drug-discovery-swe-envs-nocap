# Issue

**Title:** psi4: 1.9.1 -> 1.10

## Description

Updates Psi4 to the latest release: https://github.com/psi4/psi4/releases/tag/v1.10

Supposedly Psi4 works now with upstream LibInt2, but honestly I have now idea how. I've tried to use upstream LibInt but got runtime errors whenever integrals were calculated. Thus, I've kept the custom libint in, as does Psi4. 

With  we could enable OpenOrbitalOptimizer for Psi4 (and remove integratorxx).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2b905c550de8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.