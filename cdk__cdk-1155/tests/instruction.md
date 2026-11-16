# Issue

**Title:** Ring fill better rxn layout

## Description

Note: Merge in #1154 first! This is only for the ring fill colouring and improved reaction layout.

This patch improves aligned reaction layout and adds an option to highlight atoms/bonds and fill in small rings:

![tmp](https://github.com/user-attachments/assets/3cb09dd4-ee30-4735-8a33-ab7a510a809a)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ccbf23967029`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.