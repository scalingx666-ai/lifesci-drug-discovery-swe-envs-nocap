# Issue

**Title:** Add `$seed <int>` xcontrol keyword

## Description

Allow a user to set a specific random seed, rather than the specific value of 41 supplied by `samerand`. We now print the random seed, so this enables a user to exactly reproduce a specific metadynamics run (given the same compiler, threading, etc).

Different Fortran compilers require a different number of seed values, M. We now pass the auto generated or user selected seed through a simple random number generator. We generate M values and use these as the seeds for the production random number generation.

,

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b31754bf3c7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.