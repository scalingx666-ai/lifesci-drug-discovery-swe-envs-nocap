# Issue

**Title:** Fixed Bug in Plotting for single datapoint

## Description

Changes made in this pull request:
- moved line projection plotting to new function
- fixed bug where plotting failed with a single datapoint and the projection couldn't be calculated.


PR Checklist
------------
 - [ ] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - [ ] Issue raised/referenced?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67d5c7d24c22`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.