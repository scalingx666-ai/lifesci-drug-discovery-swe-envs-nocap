# Issue

**Title:** Fix removed np.int alias in nstates return annotation

## Description

## Summary

`mlatom/data.py` annotates the `nstates` property with the removed alias `np.int`:

```python
@property
def nstates(self) -> np.int:
```

`np.int` was deprecated in NumPy 1.20 and **removed in NumPy 1.24**. Since `pyproject.toml` pins `numpy<2`, every supported NumPy (1.24–1.26) lacks this attribute. The property returns `len(self.electronic_states)` — a builtin `int` — so the annotation was also semantically incorrect.

It doesn't crash on import only because `from __future__ import annotations` makes annotations lazy strings, but any `typing.get_type_hints()` on this class raises `AttributeError: module 'numpy' has no attribute 'int'`.

## Fix

```diff
-    def nstates(self) -> np.int:
+    def nstates(self) -> int:
```

One-line, behavior-preserving. This is the only remaining deprecated NumPy alias (`np.int`/`np.float`/`np.bool`/`np.object`) in the codebase.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `57f75d2c0482`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.