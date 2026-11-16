# Issue

**Title:** Make `.from_json` Accept File Paths

## Description

It is a common misconception that `from_json` would accept a file path to a JSON file.

This is a small update to `from_json` and `to_json` to additionally enable reading/writing JSON from/to files and file-likes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec63b4e1dceb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.