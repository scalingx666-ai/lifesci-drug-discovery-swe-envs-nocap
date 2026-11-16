# Issue

**Title:** docs: add --cycles to man page

## Description

Adds a description for the --cycles parameter to the man page.

The parameters is described in the documentation [read the docs](https://xtb-docs.readthedocs.io/en/latest/optimization.html) and in the [xtb-docs github](https://github.com/grimme-lab/xtb_docs/blob/main/source/optimization.rst) but does not occur in the man page.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `902b313678b9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.