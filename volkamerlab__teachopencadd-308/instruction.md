# Issue

**Title:** T019: Fix "No template found for residue 444 (03P)"

## Description

## Description
Fix problem described in #307 
Check: https://github.com/openmm/openmm/wiki/Frequently-Asked-Questions#template

## Todos
Notable points that this PR has either accomplished or will accomplish.
- [x] Fix template problem - how?
- [x] Remove simtk from docstrings
- [x] Revert back to CI that tests all notebooks (not only T019)

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `40584af20300`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.