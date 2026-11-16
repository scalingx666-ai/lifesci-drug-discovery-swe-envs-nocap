# Issue

**Title:** Virtual Sites Constraints, Improved Logging and Docs

## Description

## Description
- [X] Fixed constraints issue with virtual sites so that the vector lengths do not exceed their scale factor limit when summed.
- [X] Removed recursive search for log file.
- [X] Streamlined logging so it's cleaner and works better with tests.
- [X] Added some logging to dihedrals.py, outputting the fitting errors at various stages.
- [X] Moved torsion test to an argparse action.
- [X] Updated rdkit docs to new style.
- [X] Updated readme with altered install instructions and clearer cookbook.

## Todos
- [ ] Need a fix for extracting charge data before v-sites can be working properly.

## Questions
- [ ] Which other areas of QUBEKit should have improved logging?

## Status
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `816c418bc264`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.