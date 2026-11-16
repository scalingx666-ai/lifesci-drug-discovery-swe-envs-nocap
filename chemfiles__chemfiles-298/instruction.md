# Issue

**Title:** Improve XYZ format output

## Description

Using `{:g}` instead of `{}` produces nicer output:

```
# with {:g}
0.4569 1.34 4
# with {}
0.45689999999999999973423 1.34 4.0
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3b126dad2aad`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.