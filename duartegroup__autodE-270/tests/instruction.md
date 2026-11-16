# Issue

**Title:** Add exception for NEB init with <2 images

## Description

<!--
Please replace _#ISSUE_ with just e.g. #12 if this PR resolves issue 12.
-->
##  

Raises `ValueError` with `num` < 2. A NEB can reasonably be constructed with just 2 images, and is required for the `partition` method

***

## Checklist

* [x] The changes include an associated explanation of how/why
* [x] Test pass
* [x] Documentation has been updated
* [x] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7b89cd2a4b90`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.