# Issue

**Title:** fix number of OpenMP threads

## Description

This tries to fix the case when OpenMP sets automatically OMP_NUM_THREADS equal to the number of HW cores.  

Since the hwloc library is often available when using Mpich or OpenMPI, use the hwloc API to get the number of HW cores and
set OMP_NUM_THREADS=(no. HW cores/ no. processes per node).  

If the user has set the env variable OMP_NUM_THREADS, this process is not executed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `06207b9023b8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.