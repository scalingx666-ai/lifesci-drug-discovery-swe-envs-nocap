# Issue

**Title:** hide/show player

## Description

private method for now



cc @jbarnoud 

```python
view._remote_call('show', target='player')
view._remote_call('hide', target='player')
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0615ff028164`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.