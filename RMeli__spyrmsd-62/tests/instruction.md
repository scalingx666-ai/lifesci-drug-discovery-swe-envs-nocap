# Issue

**Title:** Fix number of nodes in graph-tool graphs with disconnected single nodes

## Description

## Description

Fix #61 by explicitly defining the number of vertices when creating a `graph-tool` graph from an adjacency matrix.

This PR also add a warning for disconnected graphs, but might slowing down things for something that is not really useful in standard cases (i.e. small molecules).

## Checklist

- [x] Tests
- [x] Changelog

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3c11da5f3389`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.