# Issue

**Title:** 130 add fix attribute output type

## Description

Solves 
ToDos:
 - [x] Add `output_type ` to `ChempropNeuralFP`
 - [x] Make `output_type` of `MolToMorganFP ` depend on the attribute `counted`
 - [x] Add unit tests

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `37a802940517`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.