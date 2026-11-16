# Issue

**Title:** New benchmarks for multi-core even selection tests.

## Description

bug_fix/even_selection_zero changed the Markov chains for these tests.
A note about the effect of the bug-fix has also been added.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5f5e087c2253`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.