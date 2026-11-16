# Issue

**Title:** Fix for pybind11 v3.0.3

## Description

These are the proper fixes to last week's hasty fixes.


## Description
<!-- Provide a brief description of the PR's purpose here. -->

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Delete copy constructor and assignment operator for BasisSet to prevent copying. It was trying to build this constructor and finding an incomplete class that was the cause of L2 shell build errors with pybind11 v3.0.3 . @jturney approves
- [x] The new `simple-dftd3` v1.3.0 implements “match default in Python API with CLI to require opt-in for ATM”. So 3-body not included. Mostly psi4 side-steps this setting by setting all params explicitly. The last dftd3/version test case in section III uses the `run_sdftd3` interface and hits the change. It's fine for longstanding v1.2.1 and compensated-for in the WIP QCEngine v0.50.0, but in the narrow meantime, we need to skip this test. Anyone running the `simple-dftd3` program other than through psi4 total energies (i.e., `psi4.energy("b3lyp-d3")` is in the clear) should check your versions and parameters to make sure you're using what you think you are.

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f61bbd68f99`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.