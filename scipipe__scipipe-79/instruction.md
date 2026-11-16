# Issue

**Title:** Change TempDir to Use a Hash of Task Information for the Directory Name.

## Description

Uses a hash instead of concatenating the relevant Task information to form the TempDir name.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d700a841595e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.