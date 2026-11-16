# Issue

**Title:** Even more type hinting

## Description

- Added a lot more type hints. So far only to cartesian code
- Added `py.typed` files to all sub-packages. Even those which are not yet type-hinted. The advantages outweigh the drawbacks
- Expose the `typing` module to the user. (i.e. moved from `cc._utilities.typing` to `cc.typing`.)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3458245d5fc1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.