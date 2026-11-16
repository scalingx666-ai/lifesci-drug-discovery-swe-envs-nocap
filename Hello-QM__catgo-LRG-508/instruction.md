# Issue

**Title:** fix(workflow): allow extensionless POSCAR import

## Description

## Summary

This PR fixes the workflow structure import dialog so users can select extensionless VASP structure files such as `POSCAR` and `CONTCAR`.

## Root cause

The dialog advertised `POSCAR` as a supported format, but the hidden file input used an `accept` list containing only file extensions. On Windows file pickers, extensionless files like `POSCAR` and `CONTCAR` are filtered out, so users could not select them even though the parser can handle them.

## Changes

- Removed the restrictive `accept` attribute from the structure file input.
- Updated the supported-format hint to explicitly list `POSCAR`, `CONTCAR`, and `.extxyz`.

## Validation

- Ran `corepack pnpm check`.
- Result: 0 errors; existing Svelte warnings are unrelated to this change.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a910abd9e6a9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.