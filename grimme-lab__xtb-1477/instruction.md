# Issue

**Title:** Add smooth cutoff for dispersion

## Description

This PR adapts the smooth cutoff introduced for the dispersion in dftd4 (dftd4/dftd4#362) and simple-dftd3 (dftd3/simple-dftd3#183), as well as tblite (tblite/tblite#328 and tblite/tblite#332). I also adapted the default smoothing and cutoff radii from tblite for GFN1 and GFN2. Lastly, this PR removes the weight cutoff in xtb for the dispersion. The smooth cutoff only affects large structures and is relatively minor (an Ar₃₀ chain (209 Bohr long) changes GFN1: 1.4e-7 Eh and GFN2: 4.8e-6 Eh). 

This prepares the long-term switch to using tblite for all Hamiltonians by fully aligning the xtb and tblite SCF results. Remaining changes of the cutoffs and conversion constants will be part of an upcoming PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `59c8c0d9d4c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.