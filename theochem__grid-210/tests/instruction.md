# Issue

**Title:** Default Grid Assesment

## Description

This pull-requests addresses Issue #179.
The Default rgrid was obtained from [Horton](https://github.com/theochem/horton/blob/master/data/grids/tv-13.7-5.txt). This corresponds to using the UniformInteger grid and PowerRTransform with a "fine" preset for the angular component. This is stored in grid/utils.py in a dictionary with the following:
```python
r"""
Obtained from theochem/horton/data/grids/tv-13.5.txt with the folllowing preamble

These grids were created by Toon Verstraelen in July 2013 in a second effort
to generate tuned grids based on a series of diatomic benchmarks computed
with the QZVP basis of Ahlrichs and coworkers. They are constructed to give
on average 5 digits of precision for a variety of molecular integrals, using
the Becke scheme with k=3.
"""
# Items are (rmin, rmax, npts) in angstrom, Meant for PowerRTransform
```

If the user provided rgrid as None, then it generates the default radial grid.
The following functions and their tests (with two added) were changed to have default rgrid options:
- AtomGrid.from_preset
- MolGrid.from_preset
- MolGrid.from_size
- MolGrid.from_pruned

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9d2718b38ed4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.