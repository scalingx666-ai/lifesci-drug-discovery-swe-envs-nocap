# Issue

**Title:** Fix CI for T025 and T026

## Description

## Description
Fix CI for T025 and T026 (we were `nbval`-checking cells which change over time since more structures are available in KLIFS, thus CI would fail whenever new structures come online).

## Todos
- [x] Remove `nbval` checks for cells that change (KLIFS returns); start with `nbval` checks after loading frozen dataset

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bccfe61e03b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.