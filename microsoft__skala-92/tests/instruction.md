# Issue

**Title:** Update indexing in Skala 1.1 model for faster backward

## Description

This PR introduces a change to the Skala 1.1 model that doesn't change its outputs but speeds up the torch backward pass significantly. It also changes the allowed checkpoint hashes to accept new (faster) functionals with this change, that I'll upload to Hugging Face when this is merged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e708815714b5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.