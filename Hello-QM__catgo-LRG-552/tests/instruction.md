# Issue

**Title:** fix(release): read raw sidecar archive paths

## Description

## Summary

- use PyInstaller archive viewer brief mode before normalizing Windows path separators
- retain exact verification of every redistributed legal document

## Root cause

Non-brief archive output uses repr-style escaped names. On Windows, a single path separator appears as two literal backslashes; replacing each one produced legal//... and still failed exact checks. Brief mode emits the raw single separator, which normalizes to legal/... correctly.

## Verification

- TDD RED requires -b -l before separator normalization
- 347/347 Node tests passed
- release-rights and legal-distribution verifiers passed
- git diff --check passed
- independent PyInstaller source review confirmed the repr vs brief behavior

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f4e6a151b65c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.