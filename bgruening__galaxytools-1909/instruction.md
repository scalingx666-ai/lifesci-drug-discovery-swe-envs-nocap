# Issue

**Title:** Update SegmentAnyTree wrapper to v1.2.3

## Description

## Summary

Update the 3Dtrees SegmentAnyTree Galaxy wrapper to the SAT `v1.2.3` container release.

This changes the resolved Galaxy tool version to `1.2.3+galaxy0`, keeps the predicted instance output dimension aligned with the wrapper parameter default (`predinstance_sat`), and tightens the no-GPU regression assertion to the full PyTorch error text.

## Validation

- `planemo lint tools/3dtrees_segmentanytree/segmentanytree.xml`
- `planemo test --docker --docker_run_extra_arguments "--user 1010:1012" --test_index 1 --test_output tool_test_output.nogpu.html --test_output_json tool_test_output.nogpu.json tools/3dtrees_segmentanytree/segmentanytree.xml`

The targeted no-GPU test passed by asserting the expected `RuntimeError: Found no NVIDIA driver on your system` stderr. The local Planemo environment still emits an optional `hdf5`/NumPy binary compatibility warning while loading assertion modules, but lint and the targeted test both completed successfully.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ba4cc2d8b456`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.