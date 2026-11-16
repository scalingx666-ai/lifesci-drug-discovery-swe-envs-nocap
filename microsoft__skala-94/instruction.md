# Issue

**Title:** Load Skala 1.1 rev1 artifacts by default

## Description

Use new skala-1.1-rev1 checkpoints.

Instead of the previous approach where we allow multiple hashes (old and new) for the same skala-1.1 functional, the files are now stored with a `-rev1` suffix.

Resolving now works like

```
_SKALA_VERSIONS = {
    "skala-1.0": ("skala-1.0.fun", "skala-1.0-cuda.fun"),
    "skala-1.1": ("skala-1.1-rev1.fun", "skala-1.1-rev1-cuda.fun"),
    "skala-1.1-rev0": ("skala-1.1.fun", "skala-1.1-cuda.fun"),
    "skala-1.1-rev1": ("skala-1.1-rev1.fun", "skala-1.1-rev1-cuda.fun"),
}
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `26b80ce52c58`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.