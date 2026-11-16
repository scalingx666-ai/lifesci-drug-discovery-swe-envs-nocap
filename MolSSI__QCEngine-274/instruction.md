# Issue

**Title:** Updates (Entos -> Qcore) bindings to new python interface

## Description

The Entos package was renamed to Qcore and has since received a python interface.

The only potentially controversial change is the "xTB" method was renamed to "GFN1"/"GFN0" to better reflect the current state of affairs. Since `method=XTB` is a bit like saying `method=DFT`.

@dotsdl This should be good to go with OpenFF datasets.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3a05aa8ecbca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.