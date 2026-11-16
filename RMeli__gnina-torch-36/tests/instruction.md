# Issue

**Title:** Load pre-trained GNINA default2017 and default2018 models

## Description

## Description

Partially address #33 and #35 by adding functionality to load the `default2017` and `default2018` pre-trained  GNINA models (with weights from #34 ).

The `dense` model is WIP, given the complexity of the architecture and possible problem in the `.pt` file (likely with `BatchNorm` layers). However, this PR simplify slightly the model architecture by lowering the level of nestedness.

## PR Checklist
- [x] Tests
- [ ] Documentation

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `158c229a67f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.