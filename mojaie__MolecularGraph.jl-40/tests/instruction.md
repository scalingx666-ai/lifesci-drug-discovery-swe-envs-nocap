# Issue

**Title:** Make subgraph operations more generic

## Description

This relaxes the requirements on the user to convert node and edge
index lists to `Set{Int}`, instead allowing any compatible iterator.
While not strictly necessary, it also adds specializations for `==`
that do not rely so heavily on `===` equality.

This also adds documentation and thus .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0ebba334269`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.