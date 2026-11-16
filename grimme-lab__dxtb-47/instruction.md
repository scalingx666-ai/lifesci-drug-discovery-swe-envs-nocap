# Issue

**Title:** Enable gradient calculations for SCF

## Description

- [x] make integral calculation differentiatable
- [x] add test to compare with gradient obtain from *tblite* 
- [x] check why self energy refactoring from #39 breaks backwards pass

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `456d3c80e260`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.