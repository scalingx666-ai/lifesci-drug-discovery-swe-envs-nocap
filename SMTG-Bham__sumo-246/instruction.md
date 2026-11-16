# Issue

**Title:** Numpy 2.0 compatibility tweak

## Description

Checked the code with `ruff check . --select NPY201` and this was the only required change.

```
~/s/sumo (numpy-fix)> ruff check . --select NPY201                                 (science)
sumo/electronic_structure/optics.py:259:54: NPY201 [*] `np.complex_` will be removed in NumPy 2.0. Use `numpy.complex128` instead.
Found 1 error.
[*] 1 fixable with the `--fix` option.
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a7f3f53524e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.