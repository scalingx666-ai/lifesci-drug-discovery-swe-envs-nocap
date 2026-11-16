# Issue

**Title:** Print static polarizability

## Description

Print static polarizability in properties. Before, it was calculated but not passed to the `ascii_system_properties` procedure. To be exact, the static polarizability is the imaginary frequency polarizability `alpha(iw)` at w=1e-6.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0cba606560c0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.