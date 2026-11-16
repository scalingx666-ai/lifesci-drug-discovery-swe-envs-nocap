# Issue

**Title:** Initial CIF support

## Description

This is going to be, for now, work in progress. It does not compile. But I wanted to have first feedback on it, in particular if I understand correctly what are the files to modify.

The only function I have written for now is `CIFFormat::write` 😄

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a3e308844fcc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.