# Issue

**Title:** Various small fixes and interface improvements

## Description

Main change is to refactor `eval_psp_energy_correction`, in particular move `n_electrons` out of this function, which has always felt weird.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d6ae833bb1a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.