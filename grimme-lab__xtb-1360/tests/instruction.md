# Issue

**Title:** Fix OpenMP thread memory leaks in aespot, coulomb, disp, and hamiltonian

## Description

This pull request addresses a memory leak introduced after commit #1350. When running with Intel MKL, each GFN2 call increases memory usage by roughly 300–400 MB. After about 100 iterations, XTB reaches ~50 GB of RAM usage, whereas the same system required only ~1 GB before #1350.

After this commit it seems it comes back to normal, without any performance penalty. 

The issue appears to stem from several variables that are no longer being deallocated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9d919f700ad0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.