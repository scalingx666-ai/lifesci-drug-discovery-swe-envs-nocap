# Issue

**Title:** docs: align Basic and Advanced Examples navigation and titles

## Description

## Motivation

. Adds missing example links and makes the names on the Basic and Advanced Examples pages match the tutorial titles.

### Have you read the Contributing Guidelines on pull requests?

Yes.

### Have you updated `CHANGELOG.md`?

No, this is a pure documentation fix.

## Test Plan

Checked the sidebar links, Examples pages, and titles for every Basic and Advanced tutorial. `quartodoc build` and `quarto render --no-execute` completed successfully.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `38bcf0bdb1c4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.