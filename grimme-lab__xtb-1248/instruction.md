# Issue

**Title:** Microoptimizations of scc_core

## Description

This PR introduces a set of small optimizations which speeds up each SCC iteration in 85 ms for ~600 atoms system with 1500 shells. Total speed-up is ~10% depending on system.

Tested with ifx 2025.1.

See commit messages about impact of each of optimizations.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `97a9d25005ce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.