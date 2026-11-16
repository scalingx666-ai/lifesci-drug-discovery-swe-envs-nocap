# Issue

**Title:** remove deprecated calls from InChIGeneratorTest

## Description

When working on the RInChI implementation I realized that the tests in `InChIGeneratorTest` still use deprecated methods. This might be helpful in preparation for 3.0 to be able to drop entities marked as deprecated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d7d1c3dcd89e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.