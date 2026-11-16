# Issue

**Title:** Fix #71

## Description

This is a small fix in order to be able to have one process in a workflow.

A simple additional check for the number of processes seems to work but I am not sure though if that's not a part of some larger problem related to that.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c9b4fd2c877`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.