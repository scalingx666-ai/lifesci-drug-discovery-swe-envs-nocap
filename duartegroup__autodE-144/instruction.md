# Issue

**Title:** Refactor exceptions

## Description

Refactors custom exceptions:

- All calculations now inherit from a base autodE exception (allows for broad try/except off autodE functionality)
- Fixes a typo in  `UnsuppportedCalculationInput`. While technically a backwards compatibility breaking change it's small enough to be tolerable
- Adds documentation for exception classes

- [x] Update changelog

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `191c2a121a9d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.