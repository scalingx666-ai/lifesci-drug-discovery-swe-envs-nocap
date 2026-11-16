# Issue

**Title:** Update AtomGrid

## Description

The current changes update the docstrings of `AtomGrid` to make them complete and consistent. In addition, a few argument names are changes to add clarity. Before making any further changes, I wanted to clarify a few things regarding the `AtomGrid` constructors which are exemplifiedd below:

```python
from grid.atomgrid import AtomGrid
from grid.onedgrid import GaussChebyshev
from grid.rtransform import BeckeTF

oned = GaussChebyshev(30)
rgrid = BeckeTF(1.e-4, 1.5).transform_1d_grid(oned)

# option 1 (using degrees of Levedev grid)
g = AtomGrid(rgrid, degrees=[11])

# option 2 (using atomic number & preset)
g = AtomGrid.from_predefined(rgrid, 1, 'coarse')

# option 2 (using atomic radius & sectors)
g = AtomGrid.from_pruned(rgrid, 0.5, sectors_r=[0.5, 1., 1.5], sectors_degree=[3, 7, 5, 3])
```

1. Considering the fact that the `AtomGrid.from_predefined` loaded precomputed `sectors_r` & `sectors_size`, shouldn't it just call `AtomGrid.from_pruned` upon loading the sectors information? This is not how `AtomGrid.from_predefined` is currently implemented. So, I am a bit confused.
2. In `HORTON2`, the `coarse` built-in grid specifies the radial grid points as well. See: http://theochem.github.io/horton/2.1.1/tech_ref_grids.html?highlight=insane This is not the case for `AtomGrid`, so how are we going to support `HORTOn2`-type built-in grids?

Any comments are welcomed @tczorro, @tovrstra, and @PaulWAyers.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a2bb52299621`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.