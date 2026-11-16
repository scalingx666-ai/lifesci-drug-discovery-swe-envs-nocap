# Issue

**Title:** DHS variable step size

## Description

(1) Uses multiple step sizes depending on the distance thresholds
(2) Replaces only gradient based peak detection to cubic polynomial based peak detection (both energies and gradients)


***

## Checklist

* [ ] The changes include an associated explanation of how/why
* [ ] Test pass
* [ ] Documentation has been updated
* [ ] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `598b2dc4771a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.