# Issue

**Title:** Fix DLPNO-CCSD(T) Segfault and Memory Estimate

## Description

## Description
Fixes the memory printout issues as well as `freeze_core false` segfault discussed in issue #3336 

## Dev notes & details
- [x] My code DLPNO-CCSD(T) has always operated under the assumption that diagonal pairs (i = j) are always a strong pair (treated at CC level). This is a reasonable assumption with frozen core on, but with some very low energy occupied core orbitals, this assumption may fail. My code now manually sets all diagonal pairs to be strong pairs no matter what!
- [x] For the memory printout issue, some of the memory counters, I did not initialize them to zero, leading to undefined behavior. This has also been fixed
- [x] We also set `T_CUT_CLMO` and `T_CUT_CPAO` to `1.0e-4` to match ORCA (see https://doi.org/10.1063/1.4939030). This will only affect the time it takes to compute the initial LMO and PAO integrals, and will not affect memory since integrals are built from an AO-direct algorithm!

## Questions
- [x] @loriab Should I set `freeze_core true` if the user doesn’t specify?

## Checklist
- [x] Tests added for any new features
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6520595db625`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.