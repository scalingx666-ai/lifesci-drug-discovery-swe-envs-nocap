# Issue

**Title:** Bundle Systre

## Description

* Remove the extra `make download` step and an old Bash script to run Systre.
* Use the newest available version of the [RCSR](http://rcsr.anu.edu.au/nets) for topology detection

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9645ffd8d8be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.