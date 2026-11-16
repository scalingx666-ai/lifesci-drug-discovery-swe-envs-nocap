# Issue

**Title:** Allow GFN-FF selection from xcontrol

## Description

While `$gfn method='ff'` has technically been accepted by the xcontrol parser since #188, it wouldn't actually set GFN-FF as the method to use, still requiring `--gfnff` or `--gff` to be specified on the commandline.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a45f05d39726`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.