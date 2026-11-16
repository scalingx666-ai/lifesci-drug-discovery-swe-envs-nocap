# Issue

**Title:** CEH gradients

## Description

The implementation of the numerical charge gradients `num_grad_chrg` (for CEH).
The output is written to **ceh.grad**.
@lukaswittmann, please be careful with the [output](https://github.com/grimme-lab/xtb/blob/1186b5a4b3338a78e6ebe4e95d7dec924c536e90/src/tblite/calculator.F90#L495-L497) format.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee064757917f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.