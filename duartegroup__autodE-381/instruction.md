# Issue

**Title:** pin libgfortran to 14 in CI

## Description

Temporary fix for https://github.com/duartegroup/autodE/actions/runs/14955056856/job/42009591011 until there's an upstream xtb fix

***

## Checklist

* [x] The changes include an associated explanation of how/why
* [x] Test pass
* [x] Documentation has been updated
* n/a Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `83e8b6c01e8e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.