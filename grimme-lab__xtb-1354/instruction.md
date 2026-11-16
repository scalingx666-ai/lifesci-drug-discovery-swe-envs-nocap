# Issue

**Title:** Add static windows compile to workflow and continuous delivery

## Description

This PR adds a static windows compile and packing with the necessary DLLs to the Github workflow (this should address #1062. Due to unavailability of the ifort compilers on Windows and problems with ifx, I moved it to gfortran-15. I also added the binary to the continuous delivery. 

This should then also allow for a new release with a Windows binary. @Albkat maybe we can test on a Windows machine if the binary actually works (I can only test the testsuite here).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b8197ce484af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.