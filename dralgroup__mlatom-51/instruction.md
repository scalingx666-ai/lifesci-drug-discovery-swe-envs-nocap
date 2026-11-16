# Issue

**Title:** Use shutil.copy instead of os.system('cp ...') for CV output files

## Description

The train/subtrain/validate/test output files were copied with `os.system` and an f-string-interpolated path:

```python
os.system(f"cp {tmpdirname}/itrain.dat {iTrainOut}")
```

This breaks when the output path (`iTrainOut`, …) contains spaces or shell metacharacters, and is Unix-only. Replaced the four copies with `shutil.copy` + `os.path.join` (`shutil` is already imported), so they are shell-free, robust to special characters, and portable. Behavior is otherwise unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e8fb07caf08a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.