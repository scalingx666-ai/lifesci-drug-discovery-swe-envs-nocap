# Issue

**Title:** doubletfinder: auto-generated tool wrapper (issue #1991)

## Description

This PR adds a Galaxy tool wrapper for **DoubletFinder**, an R package for detecting doublets in single-cell RNA-seq data using artificial nearest neighbors. The generated files include the tool XML, macros, and test data, addressing issue #1991. ⚠️ **Note:** the generating agent did not terminate naturally after 30 iterations, so this wrapper may be incomplete and requires manual review before merging. Please verify the tool's parameters, test cases, and dependency specifications carefully.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `59df118958c4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.