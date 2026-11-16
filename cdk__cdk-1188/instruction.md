# Issue

**Title:** Hydrogen Normalization

## Description

This overhauls the hydrogen suppression/contraction logic placing it all in one place and adding new useful functionality and fixes some corner case. We now have an enum which controls how you would like your hydrogens stored/represented it has 5 options which are summarised by this diagram (included in the JavaDoc):

![htypes](https://github.com/user-attachments/assets/6d5c451c-3aec-4e47-b06b-400ccc5edb18)


WIP as I need to think about the logic for "unsafe" a bit more.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `046a9c343f72`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.