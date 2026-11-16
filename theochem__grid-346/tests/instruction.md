# Issue

**Title:** Accept NumPy integers when indexing Grid, OneDGrid and PeriodicGrid

## Description

## Summary

Indexing a grid with a NumPy integer fails, although the same index as a Python `int` works:

```python
import numpy as np
from grid.basegrid import Grid, OneDGrid

g = Grid(np.random.rand(5, 3), np.ones(5))
g[0]                     # fine
g[np.argmax(g.weights)]  # TypeError: len() of unsized object

o = OneDGrid(np.linspace(0, 1, 5), np.ones(5))
o[np.int64(1)]           # ValueError: Argument points should be a 1-D array. points.ndim=0
```

NumPy integers come up naturally here: `np.argmax`, `np.where(...)[0][k]`, or looping over `np.arange(grid.size)`.

**Cause:** `Grid.__getitem__`, `OneDGrid.__getitem__` and `PeriodicGrid.__getitem__` check `isinstance(index, int)`, which is `False` for `np.int64`. The index then takes the slice/array path, `self.weights[index]` is a 0-d array, and the constructor rejects it.

**Fix:** check `isinstance(index, (int, np.integer))` in all three methods, and mention `np.integer` in the two `basegrid` docstrings.

## Tests

- `TestGrid.test_getitem` (1D/2D/3D subclasses) and `TestOneDGrid.test_getitem` now also index with `np.int64` and compare against the `int` result.
- `PeriodicGridTester.test_get_item` does the same for every periodic case.

The new asserts fail on `master` (13 failures across `test_grid.py` and `test_periodicgrid.py`) and pass with this change (115 passed). The full suite (`pytest src/grid/tests`) gives 735 passed, 1 skipped. `ruff check` on the touched files reports only findings already on `master`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `948ef0c97d91`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.