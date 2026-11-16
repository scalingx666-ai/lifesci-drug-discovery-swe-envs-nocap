# Issue

**Title:** gauxc: increase test timeout

## Description

Increases the test timeout for GauXC, which sometimes fails on loaded machines or slow hardware with a timeout.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `be47c29346ef`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.