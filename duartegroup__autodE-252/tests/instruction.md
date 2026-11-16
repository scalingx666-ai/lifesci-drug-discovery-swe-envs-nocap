# Issue

**Title:** Add option to change xTB parameterisation version and temperature

## Description

Adds options to change the xTB `--etemp` and `--gfn` flags from Config. Default values (None) prevent use of those flags.


***

## Checklist

* [x] The changes include an associated explanation of how/why
* [x] Test pass
* [x] Documentation has been updated
* [x] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `784b579af3ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.