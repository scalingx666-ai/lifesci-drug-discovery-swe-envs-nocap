# Issue

**Title:** Improved CRFO and PRFO optimiser

## Description

(1) Use Lagrangian multiplier weights to identify correct constraint modes in CRFO
(2) Update the molecular hessian instead of the lagrangian hessian for CRFO
(3) Optional mode-following by overlap checking in PRFO

***

## Checklist

* [ ] The changes include an associated explanation of how/why
* [ ] Test pass
* [ ] Documentation has been updated
* [ ] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cb45e539435c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.