# Issue

**Title:** fix issue 1280

## Description

Should fix issue #1280 

I compiled it using meson and ifort compiler. For me it worked then using water as an example
```
3

O 0.000000 0.000000  0.000000
H 0.758602 0.000000  0.504284
H 0.260455 0.000000 -0.872893

```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6901ac059006`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.