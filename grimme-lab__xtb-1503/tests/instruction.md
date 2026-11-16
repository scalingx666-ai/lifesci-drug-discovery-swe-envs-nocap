# Issue

**Title:** Restore pkg-config and module file in packaged release

## Description

This restores the xTB pkg-config file and versioned environment module to all bleeding-edge binary archives, matching the layout used by previous releases.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e64a481d53a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.