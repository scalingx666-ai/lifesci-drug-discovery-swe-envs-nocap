# Issue

**Title:** Feat request: Add lambda.z.time.corrxy in half.life calculation

## Description

This PR introduces a new parameter to the `pk.calc.half.life` function; `lambda.z.corrxy` which represents the correlation between the time and the log-concentration of the points involved in lambda.z estimation. The change is integrated in the documentation, summary statistics, unit tests and news.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `07381a0983b7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.