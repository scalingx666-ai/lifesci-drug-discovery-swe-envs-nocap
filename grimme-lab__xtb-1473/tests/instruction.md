# Issue

**Title:** Adapt Broyden from tblite

## Description

Performs the same fixes for the Broyden mixer as in tblite (). This includes:

- scaling of the quadrupole off-diagonal components by sqrt(2) to retain rotational invariance of the SCC solution
- SCC convergence criterion based consistently on the RMS of the full mixing vector
- Removes the last diagonalization and converges immediately as the convergence criteria are met. Consequently, the convergence is a bit less tight but now actually consistent with the convergence criterion.
- Move to cheaper linear system solve for Broyden consistent with tblite (has no practical relevance)

This prepares the long-term switch to using tblite for all Hamiltonians, by fully aligning the xtb and tblite SCF results.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3a46d03d735b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.