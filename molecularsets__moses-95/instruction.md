# Issue

**Title:** please check the required pomegranate version constraint

## Description

Apparently, removing the version constraint for pomegranate allows to install moses on a recent Ubuntu;
using 'python setup.py install --user'

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7b8f83b21a9b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.