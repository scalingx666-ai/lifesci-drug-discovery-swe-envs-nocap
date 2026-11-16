# Issue

**Title:** Return an empty LocalGrid when no point is within the radius

## Description

## Summary

`get_localgrid` crashes when no grid point falls inside the requested sphere, instead of returning an empty local grid.

```python
import numpy as np
from grid.basegrid import Grid

g = Grid(np.array([[0.0, 0, 0], [1, 0, 0]]), np.ones(2))
g.get_localgrid(np.array([5.0, 5, 5]), 0.5)
# IndexError: arrays used as indices must be of integer (or boolean) type
```

- **`Grid.get_localgrid`**: `np.array(self._kdtree.query_ball_point(...))` gives a `float64` array when the result is empty, so `self.points[indices]` raises. The fix passes `dtype=int`.
- **`PeriodicGrid.get_localgrid`**: translations with no hits are already skipped, but if *every* translation is empty, `np.concatenate(local_points)` raises `ValueError: need at least one array to concatenate`. The fix returns an empty `LocalGrid` in that case.

In both cases the result has `size == 0`, integer `indices`, `points` of shape `(0, *points.shape[1:])` and `weights` of shape `(0,)`. Integrating over it gives 0.

## Tests

- `TestGrid.test_get_localgrid_empty` covers the 1D, 2D and 3D subclasses.
- `PeriodicGridTester.test_get_localgrid_empty` covers every periodic case, wrapped and unwrapped.

Both fail on `master` and pass with this change. The rest of `test_grid.py` and `test_periodicgrid.py` gives the same result as on `master`. The six `test_get_item` failures already on `master` locally come from a warning-count assertion and are unrelated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad304ca1dda8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.