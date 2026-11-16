# Issue

**Title:** Convert testing to Conda Env instead of Conda Build

## Description

This PR moves the testing environment from relying on Conda-build
and instead creates conda envs which should speed up and simplify tests.

The trade off is the maintenance of multiple files for dependencies
going forward, but I think the benefits outweigh the costs.

Borrows from the QCFractal script from @dgasmith to spin up the
environments. Will need a careful review to make sure it meets our needs.


Supersedes and

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58ab86b27c2d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.