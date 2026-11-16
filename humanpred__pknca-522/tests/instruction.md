# Issue

**Title:** fix: use stats::sd instead of bare sd in pk.calc.half.life

## Description

Qualify the call to sd() with its namespace to avoid relying on implicit availability of stats functions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d1a382bf922a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.