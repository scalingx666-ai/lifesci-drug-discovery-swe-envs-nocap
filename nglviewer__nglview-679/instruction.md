# Issue

**Title:** FIX: exclude download image

## Description

```
# cell 1 
view

# cell 2
view.download_image

# cell 3
view
```

This will cause downloading image twice.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `83c9b40b560f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.