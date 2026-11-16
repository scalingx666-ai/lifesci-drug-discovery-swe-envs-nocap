# Issue

**Title:** Now builds on Ubuntu 16.04

## Description

Requires Ubuntu Qt package, Ubuntu boost test package, new local build of cmake, cuda sdk installation

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9e3bfb55c8ff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.