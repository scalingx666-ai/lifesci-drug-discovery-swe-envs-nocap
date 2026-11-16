# Issue

**Title:** Fix --output_format pdb with --model boltz1

## Description

Currently pdb format outputs crash when using --model boltz1. This patch prevents this and enables --output_format pdb for both boltz1 and boltz2 modes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8f23a42cbe35`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.