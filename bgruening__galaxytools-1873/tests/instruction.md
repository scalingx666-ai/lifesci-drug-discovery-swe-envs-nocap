# Issue

**Title:** Update 3DTrees SmartTile to v2.1.0

## Description

## Summary

Updates the 3DTrees SmartTile Galaxy wrapper to use SmartTile v2.1.0 and clarifies that the chunk-size parameter also controls stalled-COPC laspy fallback extraction.

## Validation
- SmartTile v2.1.0 source release and GHCR image publish completed successfully upstream.
- Earlier local Galaxy tool test for 3dtrees_smart_tile passed: 4 passed, 0 failures/errors/skips.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `494f2344e374`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.