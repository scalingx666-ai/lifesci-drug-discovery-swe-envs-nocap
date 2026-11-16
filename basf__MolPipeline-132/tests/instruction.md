# Issue

**Title:** move version from pyproject.toml to __init__

## Description

Solves 

Move the package version from the pyproject.toml to molpipeline/__init__.py. Now we can do things like:

```python
import molpipeline
print(molpipeline.__version__)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `75eb7e4fe48b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.