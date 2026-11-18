# Issue

**Title:** GitHub CI Workflow Enhancements Part 6

## Description

This PR adds support for builds with the Portland Group Inc. (PGI) compilers, now more recently available through the NVIDIA NVHPC SDK.  Also, Github CI tests are included using the NVHPC v25-1 on the most recent x86_64 Ubuntu runner.

PGI support was also tested for the following configuration on the MSU HPCC:
- Hardware: amd20 node, V100 GPUs
- NVHPC v23-7 (bundled with OpenMPI v3.1.5, CUDA v12.1.1)
- Full test suite passing for the following QUICK versions: seiral, MPI (1 and 2 processors), CUDA, MPI+CUDA (2 GPUs)

Limitations / Notes:
- Github CI tests are built using the bundled BLAS/LAPACK and OpenMPI libraries for the NVIDIA NVHPC SDK (see the shell variables set in the Github workflows for further details)
- At some point after the NVHPC v23-7 release, the bundled PGI compilers stopped being identified by CMake by the `"PGI"` string and started being identified by `"NVHPC"` (see the CMake variables `CMAKE_{C,CXX,Fortran}_COMPILER_ID` for further details).  This might also depend on the CMake version.  For now, bump the minimim required CMake version from 3.8 to 3.11 in light of this and applicable CMake code clean up.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9ce88d5905a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.