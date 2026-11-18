# Issue

**Title:** Fix notebook SVG ID collisions

## Description

Uses globally unique SVG ID prefixes so inline notebook renders cannot reuse gradient or definition IDs from earlier outputs.

  .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `388e6996442e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.