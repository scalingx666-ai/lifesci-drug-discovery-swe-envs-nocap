# Issue

**Title:** Added TDC scoring component

## Description

This adds a scoring component for oracles from Therapeutic Data Commons, currently restricted to only permit the 23 oracles included in the Practical Molecular Optimization benchmark for _de novo_ drug design.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b8c507fe896`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.