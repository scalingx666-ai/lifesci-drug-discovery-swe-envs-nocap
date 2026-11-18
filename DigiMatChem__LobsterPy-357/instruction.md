# Issue

**Title:** Cli updates

## Description

#  and #328

## **Note**: Failing tests in CI are due to the pymatgen depreciation of some methods and have nothing to do with `LobsterPy` / pymatgen `LOBSTER` parsers/changes in this PR.

# Todo

- [x] coloured icoxx distance plots via CLI 
- [x] add option to get BWDF plots
- [x] Update cli docs and tutorials to showcase BWDF  / ICOXX distance plotting 
- [x] Option to save raw plot data of relevant (I)COXX as jsons

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7b36d90159d6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.