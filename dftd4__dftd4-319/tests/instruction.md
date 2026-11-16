# Issue

**Title:** Dynamic load balancing for ATM

## Description

The workload in the triple loop of the ATM term is maximally unbalanced:
- first iteration: all loops have a length of 1
- last iteration: all loops have length `<number of atoms>`

Currently, OMP scheduling is decided at runtime (`OMP_SCHEDULE` environment variable). Depending on the compiler and whether the environment variable is set or not, `static` scheduling is likely selected (, [source 2](https://stackoverflow.com/questions/61638747/default-scheduling-in-openmp-gcc-compiler)). Given the unbalanced workload, `dynamic` scheduling should always be faster here.

Instead of having the user figure this out, we now explicitly employ `dynamic` scheduling for the ATM term.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `218b56c76d62`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.