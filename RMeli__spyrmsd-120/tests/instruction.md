# Issue

**Title:** Update GitHub actions and pre-commit configuration

## Description

## Description

Update GitHub actions. Avoids the following warnings:

> Node.js 16 actions are deprecated. Please update the following actions to use Node.js 20: actions/checkout@v3, codecov/codecov-action@v3.

## Checklist

- [ ] Changelog

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5b01c942997e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.