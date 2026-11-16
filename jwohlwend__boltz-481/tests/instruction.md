# Issue

**Title:** Allow case-insensitive input suffixes and correct docstring mismatch

## Description

**Description:**
This PR makes two small, self-contained improvements:

- Input file suffix matching is now case-insensitive (e.g. .YAML is accepted)
- Fixed a mismatch between the docstring and the actual default for max_msa_seqs (4096 → 8192)

These changes were originally part of PR #461, but are split out here for clarity.
Let me know if you'd like anything adjusted!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ac1c8582d61a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.