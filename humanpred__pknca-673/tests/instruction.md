# Issue

**Title:** style: drop the redundant stringsAsFactors = FALSE from data.frame() calls

## Description

PKNCA depends on R >= 4.1, where data.frame() already defaults to stringsAsFactors = FALSE.  expand.grid() still defaults to TRUE, so its calls keep the argument (the simulation design indexes lists by the scenario's route, which a factor would turn into its integer code).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e3b729e51f37`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.