# Issue

**Title:** sharc: 3.0.2 -> 4.0.2

## Description

Updates SHARC to its latest version. The python programs require much more python packages now, including OpenMM, PySCF and torch, making it a quite heavy closure. But whatever ... :smile: HDF4 and NetCDF4 are also of course still included.

The executables all seem to run, but I have not idea about SHARC, so @markuskowa could you test this? :innocent:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b16875f2f72b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.