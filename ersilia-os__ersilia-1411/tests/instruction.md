# Issue

**Title:** Generalize Standard Run

## Description

The aim of this PR is to generalize standard run to work with any type of model server response and be able to serialize a CSV output file. In addition to that, other changes introduced through this PR are:

- We can now calculate the output csv header from a predefined example file, in addition to the standard csv output file
- The is_ready function from the StandardCSVRunApi class is removed, and only the is_amenable function is kept because the checks in the latter were a superset of the ones in is_ready.
- Unused code is removed
- The `run` method no longer has a try_standard parameter because standard run is the default behavior.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `92c9d8e5a64b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.