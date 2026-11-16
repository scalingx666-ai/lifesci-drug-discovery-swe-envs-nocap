# Issue

**Title:** Fix a bug when parsing PROCAR with spin polarsation

## Description

The list of parsed kpoints should only be updated after parsing is completed, otherwise the second set of spin down projections is completely skipped, e.g. parsed PROCAR only contains the first spin.

I also moved the normalisation to a separate method so it is possible to not have the weights normalised, as VASP's projected weights are known to not sum to 1 for a given band. Although for unfolding we want to have it normalised in order to make the visualisation better.

Should be able to fix #30 and #31

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a8c914690288`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.