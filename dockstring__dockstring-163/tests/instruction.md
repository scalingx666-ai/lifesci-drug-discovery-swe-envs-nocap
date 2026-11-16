# Issue

**Title:** Various PyPI-related fixes.

## Description

Contains a few fixes/changes related to PyPI:

1. In the project README, mention the installation method from PyPI (`pip install dockstring`)
2. Fix authors list. First, I added Miguel's name without the accents. Second, on PyPI the release listed
  Gregor as the author but gave Miguel's email. It looks like this is a
  .
  To fix this I removed our emails. People can figure out how to contact us if they really need it.
3. Added missing entries in the CHANGELOG.
4. Added some extra metadata to pyproject.toml, including the github homepage.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7e36d2311303`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.