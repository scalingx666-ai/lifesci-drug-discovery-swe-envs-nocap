# Issue

**Title:** ORCA executable check vs gnome screen reader using SCF keyword in binary

## Description

Fixes a bug as mentioned in #1308 with a better sanity check. This now checks the orca binary contents for the keyword "SCF" as this should be specific enough to discriminate it from the GNOME screen reader binary.
Also formatted the source file.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dabf3071c0cf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.