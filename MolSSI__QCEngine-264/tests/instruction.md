# Issue

**Title:** Turbomole energy fix, Hessian, Memory managment

## Description

##  Description
Receiving the paper Draft led me to revisit the TurbomoleHarness. As my own code [pysisyphus](https://github.com/eljost/pysisyphus) also supports QCEngine I noticed a bug. In gradient/Hessian calculations the current_energy wasn't set in the output properties, only the repsective energy derivative was returned ... Now the the runner uses "build_atomicproperties" and "build_out" from qcvar_identities_resources to be more consistent.

Furthermore I added support for Hessian calculations (analytical via aoforce for HF/DFT and numerical via NumForce via ricc2). Corresponding tests are provided. The Harness now also has basic memory management.

## Changelog description
Fixed missing current_energy in gradient calculation, added basic memory management and support for Hessian calculations.

## Status
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `236156f3101d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.