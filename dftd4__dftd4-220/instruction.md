# Issue

**Title:** Add D4 parameters for RSHs

## Description

Add parameters for the following range-separated hybrid functionals:

- CAM-QTP(01)
- LC-&omega;PBE
- LC-&omega;PBEh
- &omega;B97M-rev
- &omega;B97X-3c
- &omega;B97X-rev (from [&omega;B97X-3c paper](https://doi.org/10.1063/5.0133026))

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0627ec8939b0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.