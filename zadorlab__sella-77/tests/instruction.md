# Issue

**Title:** Fix compatibility with scipy 1.18+ LinearOperator

## Description

scipy 1.18.0 added array namespace support to LinearOperator, which requires the _xp attribute set by `LinearOperator.__init__`. Call `super().__init__(dtype, shape)` instead of setting `self.shape` and `self.dtype` directly in all LinearOperator subclasses.

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e4626c96262`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.