# Issue

**Title:** qmake file fixes #1

## Description

qmake file to compile the c++ code.

Hardcodes cuda location to /usr/local/cuda.

As a sorry for being smarmy about QT dependence.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `973d54251b7b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.