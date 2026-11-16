# Issue

**Title:** Migrate 3D visualization from mayavi to PyVista

## Description

## Summary

- Replace **mayavi** with **PyVista** as the preferred 3D backend for all plotting methods (`plot_contour3d`, `plot_mcontour`, `plot_field`)
- **Backward compatible**: mayavi is kept as a legacy fallback — existing mayavi users continue working without changes
- Add `_build_structured_grid()` helper that builds a proper `pyvista.StructuredGrid` using POSCAR lattice vectors, correctly handling **non-orthogonal cells** (hexagonal, monoclinic, etc.)
- Fix `scipy.integrate.simps` → `simpson` compatibility with scipy 1.14+
- Add `pyvista>=0.42.0` to dependencies
- Remove outdated Canopy installation instructions

## Backend selection logic

```
pyvista installed → use PyVista (recommended, supports non-orthogonal cells)
       ↓ not installed
mayavi installed  → use mayavi (legacy fallback)
       ↓ not installed
     warning → pip install pyvista
```

## Motivation

- mayavi is unmaintained and hard to install, especially on Windows (#18)
- mayavi depends on PySide/PyQt4 which are also abandoned (#4)
- Old `plot_contour3d` assumed orthogonal cells, causing wrong visualizations for hexagonal cells (#8)
- PyVista is actively maintained, easy to install, and natively supports non-orthogonal grids

## API Compatibility

All public method signatures are preserved — same kwargs, same behavior.

## Fixes

-
-
-

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a48bb43842bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.