# Issue

**Title:** excretion parameters ERTLST, ERTMAX (reimplementation of #475)

## Description

The PR re-introduces the excretion rate parameters: the maximum excretion rate (`ermax`), the time of maximum excretion rate (`ertmax`), and the time of the last measurable excretion rate (`ertlst`). It also adds supporting infrastructure for these parameters, such as new unit types, helper functions for missing data messages, and comprehensive tests. Additionally, some code cleanup and improvements to missing data handling are included.


The purpose is to keep working in this PR to solve the invisible issues that happened after merging #475 related with:

- use of arg `allow.tmax` for `ertmax` parameters. Perhaps the appropiate would be to create a new arg that by default is the same as `allow.tmax` (@billdenney  ?)
-  make sure the parameters can be computed alone when calling `pk.nca` (test already implemented in `main`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `afe8b662d2c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.