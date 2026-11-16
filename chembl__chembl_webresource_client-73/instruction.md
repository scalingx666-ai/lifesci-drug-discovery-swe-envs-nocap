# Issue

**Title:** Check default format for svg+xml

## Description

This will resolve #71 and allow for parsing xml data as before.

For example the command:
```python3
new_client.target.only(['organism'])[0]['organism']
```
 currently throws an exception due to the response being a xml string, rather than a dictionary.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `758e1e1f3dbb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.