# Issue

**Title:** write new orbital optimization tutorial that uses ffsim

## Description

The idea is to deprecate `fermions.optimize_orbitals` and just have this guide showing the user how to do it themselves. This is more flexible because the user will probably want to use alternative diagonalization solvers. Also, it uses the orbital optimization function in ffsim so we don't need to maintain such code ourselves.

Followup: deprecate `fermions.optimize_orbitals` and close related issues and pull requests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c289f024773d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.