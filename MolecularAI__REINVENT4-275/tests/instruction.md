# Issue

**Title:** Fixed libinvent example SMILES attachment point numbering

## Description

Fixed the Libinvent example to start attachment point numbering from 0 instead of 1 (#274)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `85ccab2500a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.