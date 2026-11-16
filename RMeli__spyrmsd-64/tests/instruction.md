# Issue

**Title:** Expand node attribute types for graph-tool

## Description

## Description

Fix #63. Add support for more types as node properties (including strings) with `graph-tool`. This allows to perform node matching using not only atomic numbers but also elements, atom types, ..., which is already the case for `networkx`.

TODO:
- [x] Change signature from `atomicnums` to `atomprops` (or similar)

## Checklist

- [x] Tests
- [x] Changelog

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9be79d7b433b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.