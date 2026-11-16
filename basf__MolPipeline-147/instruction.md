# Issue

**Title:** Add chemprop multiple/multi-target regression

## Description

Add functionality to use chemprop for multiple regression.

This is done by exposing the `n_tasks` parameter in the `ChempropRegressor`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5149422f8b2d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.