# Issue

**Title:** StreamArgs.copy() breaks lisp

## Description

Hello Caleb,

A user class derived from StreamArgs or EnergyStream will fail to properly copy the object.
Instead of direct construction the type we leave it to the class itself to construct the correct type.

cheers simon

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e10dfc9b9f14`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.