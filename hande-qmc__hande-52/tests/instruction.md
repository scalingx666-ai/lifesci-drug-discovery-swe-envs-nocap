# Issue

**Title:** Fix continuous integration

## Description

Fixes CI stack for use of newer GCC compiler. I have also set up integration with Circle CI where we can use a custom Docker image to specify the build environment. There is one test failing on Travis: `ifciqmc/np4/H2O-RHF-cc-pVTZ-non-block-hdf5-system` and what's worse it seems to be intermittent.

The status on Circle CI is here: https://circleci.com/gh/flaks-qmc/hande/tree/fix-travis
I think I can only update the badge when this PR is accepted and the integration is set up for this repo (now it's done on my fork)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `20160be3e66f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.