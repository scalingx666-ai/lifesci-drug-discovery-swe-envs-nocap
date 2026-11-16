# Issue

**Title:** Constants update

## Description

<!--
Please replace _#ISSUE_ with just e.g. #12 if this PR resolves issue 12.
-->
##

Update the physical constants to agree with the CODATA 2022 standards. Source: https://physics.nist.gov/cuu/Constants/index.html

Derived units derived from the constants. Comments include the corresponding uncertainties, unless the value is exact.

***

## Checklist

* [x] The changes include an associated explanation of how/why
* [x] Test pass
* [ ] Documentation has been updated
* [x] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a449a2db012e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.