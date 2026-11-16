# Issue

**Title:** Implement parallelization for hydrogen bond list setup in gfnff_hbset and gfnff_hbset0

## Description

Now, subroutines gfnff_hbset and gfnff_hbset0 now are parallelized using OpenMP. The idea is to collect information about connections in OpenMP-thread-specific arrays and then dump it to global arrays. I did not test it a lot, but tests now 1.5 s faster on my laptop for 4 threads, mainly from xtb/gfnff test.

I've also reformatted source code of these routines. 

Alternative approach is #1240.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c3524d87cedd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.