# Issue

**Title:** Init some variables in relaxation engine

## Description

At 
https://github.com/grimme-lab/xtb/blob/41059b44d84a07dfd99a051e4409ef654faca939/src/relaxation_engine.f90#L1418-L1419
the reading of uninitialized variable may generate SIGFPE. This patch defines `lat_gnorm` as well as other variables related to optimization of cells to avoid such behaviour.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fc10da86ee73`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.