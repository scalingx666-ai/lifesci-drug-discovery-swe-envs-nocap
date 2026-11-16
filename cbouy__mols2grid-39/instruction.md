# Issue

**Title:** Fix text search

## Description

.

Text searches containing any of the following regex characters `-[]{}()*+?.,\^$|#` would automatically return an empty grid, preventing searching for CAS numbers and any other identifier or text containing the above characters.

This has been temporarily patched until a proper fix is released in the underlying `list.js` library.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7723b2460ea7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.