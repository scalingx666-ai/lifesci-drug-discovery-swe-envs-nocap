# Issue

**Title:** Membrane builder tutorial

## Description

I added a membrane builder tutorial to advertise this as well.

In the process I also fixed some issues:
a) psfgen `call` was not logging the `stderr` to the file
b) psfgen fails in some locales so calling it with `LC_ALL=C` is safer
c) removed unused files and code
d) renamed private functions to start with `_`
e) `listLipids()` now also prints the location of the database file which I also moved to the lipids folder.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1bbc24ce9972`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.