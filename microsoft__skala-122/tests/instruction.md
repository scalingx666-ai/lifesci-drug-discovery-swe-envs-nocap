# Issue

**Title:** Restructure pipelines

## Description

## Summary

Reduce unnecessary GitHub Actions runs by limiting workflows to `main` and
triggering them only when their relevant inputs change.

Split the existing examples pipeline by consumer so GauXC changes do not run
the direct LibTorch and FTorch integrations, and model-example changes do not
start the full GauXC matrix.

## Changes

- Restrict Tests, Model benchmarks, GauXC examples, and Model examples to:
  - pull requests targeting `main`
  - pushes to `main`
- Add workflow-specific path filters.
- Reuse each path list between `push` and `pull_request` with YAML anchors.
- Had to fix the cpp model example as it was not CI tested

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dca80684a815`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.