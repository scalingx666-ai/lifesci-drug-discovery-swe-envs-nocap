# Issue

**Title:** Potential fix for code scanning alert no. 11: Unused import

## Description

Potential fix for [https://github.com/dftd3/simple-dftd3/security/code-scanning/11](https://github.com/dftd3/simple-dftd3/security/code-scanning/11)

To fix an unused import, remove the unused name from the import statement (or delete the whole import if none of its names are used). This reduces unnecessary dependencies and keeps the module clean.

In this file, the problematic line is `from pytest import approx, raises, mark`. According to CodeQL, only `mark` is unused. The best minimal fix that preserves all existing functionality is to keep `approx` and `raises` (which are presumably used elsewhere in the file) and drop `mark` from the import list. No other changes are required.

Concretely:
- In `python/dftd3/test_interface.py`, at line 28, change `from pytest import approx, raises, mark` to `from pytest import approx, raises`.
- No new methods, imports, or definitions are needed.

_Suggested fixes powered by Copilot Autofix. Review carefully before merging._

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `80b548db6583`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.