# Issue

**Title:** Refactor

## Description

Hi Caleb,

This pull request refactors the utils.py module to a subpackage. I'm planning on doing a bit more work on the TDependentProperty and TPDependentProperty objects later, so separating these out to separate modules should help me work much faster.

I put miscellaneous functions in a module called "functional.py". Not sure if you have any better ideas to name this module...

Thanks!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a259e48a3100`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.