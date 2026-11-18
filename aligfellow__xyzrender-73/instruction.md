# Issue

**Title:** Add graph style preset and rendering mode

## Description

## Summary

This adds a new `graph` rendering style to `xyzrender`.

## What changed

- Added a built-in `graph` preset
- Wired graph-specific config into rendering
- Updated SVG drawing so graph nodes/edges match the cleaner minimalist look
- Kept graph edges visually consistent and improved node layering/readability
- Added docs/README updates plus a gallery example image
- Added tests for graph preset behavior and config defaults

## Notes

- This branch was merged with latest `main` before opening the PR draft.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8a28a7bcb200`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.