# Issue

**Title:** Use smaller archives for external dependencies

## Description

This reduces the zlib and tng archives, bringing the size of chemfiles archive from 16MiB down to 6MiB. This was prompted by crates.io refusing to upload the crate for chemfiles-sys.

I have also added a test to catch any file size regression.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7f8ad8d37c4c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.