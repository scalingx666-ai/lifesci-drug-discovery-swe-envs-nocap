# Issue

**Title:** [widget] use Integer traitlet to handle long on Py27

## Description

The Integer traitlet handles both int and long on py27
and of course int on py3.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cce3f75b1a67`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.