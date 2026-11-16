# Issue

**Title:** Ensure atom symbols are printed in property tables

## Description

## Problem
On macOS ARM, atom symbols were missing from D4, Mulliken, spin-population, FOD, and Wiberg/Mayer property tables. The underlying data remained correct. See issue #1448 .

## Fix
TMolecule%sym is a deferred-length allocatable character array, but the routines responsible for reporting its values declared the array as an explicit-shape assumed-length array (sym(n)). This caused incorrect argument handling with the macOS+ARM Fortran compiler. The updates here now use the array shape taken from the caller (assumed-shape) (sym(:)), preserving the symbols correctly.

This should resolve issue #1448 

## Testing
Built xtb on ARM64 with GCC 15.3 and reproduced issue #1448. After fix was applied, verified that D4, Mulliken, spin-population, and Wiberg/Mayer tables correctly display the atom symbols.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f2a2ba903212`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.