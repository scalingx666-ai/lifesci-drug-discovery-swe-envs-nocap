# Issue

**Title:** Updated docutils version constraint to resolve dependency conflict and Typo in README.md

## Description

### Fix documentation dependency conflict
When we install documentation dependancies with `pip install '.[doc]`, It gets stuck in an infinite loop due to incompatible version constraint.

### FIX
Updated docutils version constraint from =0.16 to >=0.20 to allow modern, compatible versions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e652038d54de`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.