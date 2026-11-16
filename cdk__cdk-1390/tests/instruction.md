# Issue

**Title:** Avoid IChemObjectListener proliferation when finding rings

## Description

Calling Cycles.*.toRingSet() again and again on the same container causes the listeners to proliferate, add a test case to demonstrate

To avoid the listener proliferation:

1) Use a set to store the listeners, each one should only occur once
2) Remove them when we create the IRingSet in Cycles.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4b6c9bb4cdc4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.