# Issue

**Title:** Fix ebond charge scaling for large negative factors qafac

## Description

For systems with large partial charges (such as mindless molecules), the charge factor `qafac` for the bond parameter `neigh%vbond(3,:)` can become a large negative number. This results in the exp() to get infinite at https://github.com/grimme-lab/xtb/blob/7fc982ac70f5b1d37479f4fc33913fb1e9500aac/src/gfnff/gfnff_ini.f90#L1318 and https://github.com/grimme-lab/xtb/blob/7fc982ac70f5b1d37479f4fc33913fb1e9500aac/src/gfnff/gfnff_ini.f90#L1342 which was not properly handled.
I implemented an if condition that assigns the asymptotic limit for large exponents.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7fc982ac70f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.