# Issue

**Title:** Fix precission in tabulated radii and remove stale broyden damping

## Description

Fixes the precision of tabulated radii and electronegativity to double precision (consistent with tblite), and removes the stale change in Broyden damping for small gaps. The change is small (order 1e-10 for the GFN2-xTB energy)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b188560cc531`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.