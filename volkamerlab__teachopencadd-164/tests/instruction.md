# Issue

**Title:** Fix CLI bug (greeting printed twice)

## Description

## Description
The TeachOpenCADD greeting is printed twice when using `teachopencadd` or `teachopencadd -h`. Remove the greeting in these instances (easier than reducing the output to one greeting).

## Todos
- [x] Fix CLI greeting bug (printed doubled) for `teachopencadd -h`
- [x] Add test

## Questions
None.

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cbf005e52cbf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.