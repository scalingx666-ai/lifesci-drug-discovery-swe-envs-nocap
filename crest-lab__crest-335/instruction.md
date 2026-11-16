# Issue

**Title:** Update of GitHub workflows

## Description

Update GitHub workflows builds to test different gnu versions. Also now tests the cmake build on macOS.

Furthermore, enabled static builds via cmake and use this to create a continuous release static binary using GNU/openblas, which will now be uploaded automatically alongside the meson build.

Updated the README.md accordingly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3fa26ab1b6b8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.