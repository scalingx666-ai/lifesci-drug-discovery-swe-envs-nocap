# Issue

**Title:** Enable `parse_system` for systems with `Dual` positions

## Description

. 

**Quick summary:**
`parse_system` fails when atom positions contain `ForwardDiff.Dual` numbers but the lattice is `Float64`. This is because `DFTK.parse_system` determines the type only based on the lattice.

**Solution:**
Determine the type `T` not just from the lattice, but from both the lattice and the positions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `85669b7a1410`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.