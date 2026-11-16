# Issue

**Title:** Docs and versioner integration

## Description

I attempted to start the "next steps" documentation so that users have a set of directions to follow to get all of the integrations up and running. This PR also integrates versioner into the project so that both `project.__version__` and `project. __git_revision__` work as expected.

I would not mind doing quick iterations on this as I may or may not get a chance to work more on these pieces for a bit. Please feel free to pull in at will.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fac6b8b8dbfc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.