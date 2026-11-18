# Issue

**Title:** Fix cli inconsistency

## Description

This pull request makes a minor adjustment to the default behavior of the CLI's automatic analysis and updates the corresponding test to reflect this change.

- CLI behavior update:
  * Changed the default value of the `--noisecutoff` argument in `get_parser` from `None` to `0.1`, ensuring that a cutoff is always applied unless specified otherwise.

- Test update:
  * Updated the `test_cli_interactive_plotter_coops` test to explicitly provide a `--noisecutoff` value, aligning the test with the new default behavior.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `717c6e85ac70`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.