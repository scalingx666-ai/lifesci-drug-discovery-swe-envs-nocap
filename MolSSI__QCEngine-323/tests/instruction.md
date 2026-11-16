# Issue

**Title:** bugfix: 'N Atoms' is now set in qcvars for grad/Hessian calcs

## Description

## Description
The update to 0.20.0 broke the Turbomole harness, as 'N ATOMS' was missing in qcvars, when derivatives of the energy were calculated. This line led to an exception:

https://github.com/MolSSI/QCElemental/blob/36c5e0d3de3655fe02c42c4c1fe52eb4ba933c54/qcelemental/models/results.py#L279

## Changelog description
`qcvars['N ATOMS']` is now set for gradient and/or Hessian runs, so the AtomicProperties can be now be properly created.

## Status
- [ ] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `78bd7d22a243`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.