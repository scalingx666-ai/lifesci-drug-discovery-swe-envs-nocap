# Issue

**Title:** Fix Fold-CP confidence synchronization for multi-sample inference

## Description

## Summary

This PR fixes a Fold-CP confidence-head synchronization issue that can occur when running distributed inference with multiple samples and/or multiple model seeds.

In the previous implementation, non-output ranks could finish the confidence path earlier than rank 0, while rank 0 still needed to merge and write final confidence outputs. For inputs whose token length is not evenly divisible by the CP mesh, this could surface as a late-stage hang or communication-size mismatch in the confidence output path.

The fix keeps all Fold-CP ranks synchronized through the confidence stage, and ensures that output merging is only performed for the final output-producing model seed. This preserves the normal single-output behavior while avoiding extra output work on intermediate/non-output seeds.

## Changes

- synchronize Fold-CP confidence ranks before final output handling
- skip confidence output merging on non-output model seeds
- keep final confidence output writing on the output-producing seed only
- add focused regression coverage for multi-sample / multi-model-seed Fold-CP confidence inference

## Tests

- verified the focused Fold-CP confidence synchronization regression test
- verified the non-divisible-token confidence path with CP=4

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `266ce4c49d49`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.