# Issue

**Title:** Opt options

## Description

## Description
Adds new optking options to `read_options.cc`. Adds soon to be added `OPT_COORDINATES CUSTOM` option.

## User API & Changelog headlines
- [x] Default TS search algorithm is now RS_I_RFO

## Checklist
- [x] opt16 now by default tests with RS_I_RFO (old algorithm still tested by optking's test suite)
- [x] `-L opt`

## Status
- [x] Ready for review
- [ ] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1813c0c31e30`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.