# Issue

**Title:** Protocols

## Description

This PR starts protocols for discussion. Items:
1) Should protocols be complex? Right now we just trim data, but could they be used to specify that we require only the final orbitals in an optimization?
2) Should the protocols automatically trim data without warnings?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eddb28d72a06`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.