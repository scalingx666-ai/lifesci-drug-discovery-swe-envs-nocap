# Issue

**Title:** version + symlink

## Description

```python

pip install -e .
nglview install --symlink
```

create development version to edit both python and javasript code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f37eceeb563a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.