# Issue

**Title:** Switch to Makie 0.24

## Description

The most recent release of the Makie family was a major breaking change, introducing the new `ComputeGraph` architecture and eliminating `MakieCore` as a separate package. This commit updates MolecularGraph to be compatible with Makie 0.24, which includes:
- Creating a new extension package `MakieExt` to hold the code that previously leveraged `MakieCore`
- Updating the drawing recipes for the new API

Note: I expect the tests to fail due to the name collision described in #146. I have verified locally that this passes tests if merged onto that branch.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `78a328d793e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.