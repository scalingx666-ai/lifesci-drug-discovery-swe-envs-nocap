# Issue

**Title:** Fix MeanAggregation ONNX path with sum/count

## Description

Replace scatter_reduce(mean) with an ONNX-safe sum/count aggregation. Bond message-passing dynamic shapes were already addressed separately.

## Description
Include a brief summary of the bug/feature/etc. that this PR seeks to address

## Example / Current workflow
Include a sample workflow to either **(a)** reproduce the bug with current codebase or **(b)** showcase the deficiency does this PR seeks to address

## Bugfix / Desired workflow
Include either **(a)** the same workflow from above with the correct output produced via this PR **(b)** some (pseudo)code containing the new workflow that this PR will (seek to) implement

## Questions
If there are open questions about implementation strategy or scope of the PR, include them here

## Relevant issues
If appropriate, please tag them here and include a quick summary

## Checklist
- [ ] linted with flake8?
- [ ] (if appropriate) unit tests added?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8d9887a243d5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.