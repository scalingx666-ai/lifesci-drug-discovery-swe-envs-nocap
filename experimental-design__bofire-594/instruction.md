# Issue

**Title:** Remove cvxopt

## Description

As discussed, I removed the dependency to `cvxopt`. 

- Converted the QP-solver in the `LinearProjection` class to `cvxpy`, which is already used elsewhere.
- Created Unit-tests for `LinearProjection`
- Moved the definitions for the full optimizer tests in `test_optimizer.py` to `conftest.py`

The unit-tests are not exhaustive, but cover most of the functions. The other classes in `utils.py` are not included in the new tests. That could be added in the future.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `83c01a87d767`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.