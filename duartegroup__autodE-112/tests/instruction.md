# Issue

**Title:** Gaussian wrapper bugfix 🐞

## Description

Fixes Hessian extraction from calculations where a "Input orientation" block is not printed in the output file, which seems to be possible for some Gaussian 09 calculations.


- [x] Update changelog

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `424bb2ae7128`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.