# Issue

**Title:** Add support for dense models and GNINA default model

## Description

## Description
Thanks to @drewnutt #43 , the correct weights for the `dense` models are now available, which allow to support the `dense` models alongside `default2017` and `default2018`. More importantly, this allows to build the `default` model ensemble, thus reproducing all results obtained with GNINA.

## PR Checklist
- [x] Tests
- [x] Documentation

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b768a9e5d67`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.