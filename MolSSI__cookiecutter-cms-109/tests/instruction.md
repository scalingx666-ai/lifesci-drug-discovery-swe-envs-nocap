# Issue

**Title:** Remove default.profraw if its found

## Description

There are not too much data on exactly what this is, or what conditions
generate it. I cannot reproduce this locally, but users are reporting
it, so I added a function to remove if found and added to the .gitignore

From what I can read, its some profiling data output from the LLVM
compiler for code coverage. There are some consistent reports about it
being in Xcode 9 only, but not enough to really pin this down.

In any case, this should prevent the file from sticking around if its
there.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8bb9fdc541af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.