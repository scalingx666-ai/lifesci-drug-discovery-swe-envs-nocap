# Issue

**Title:** jupyterlab: Try to build its extension. OK

## Description

```
cd js
npm install --save
cd ../
juypter lab build ./jslab
```

Not 100% sure. :d

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d314815da76`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.