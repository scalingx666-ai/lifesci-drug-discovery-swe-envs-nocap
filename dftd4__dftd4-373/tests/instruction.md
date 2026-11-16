# Issue

**Title:** fix: convert ASE unit constants to float to fix broken arithmetic

## Description

ASE changed `Bohr` and `Hartree` in `ase.units` from plain floats to unit objects, breaking `float * unit` arithmetic (e.g. `60.0 * Bohr`) at module import time and causing `dftd4.ase` to fail to import entirely.

## Change

- **`python/dftd4/ase.py`**: Cast `Bohr` and `Hartree` to `float` immediately after import so all downstream arithmetic remains valid regardless of ASE version:

```python
# before
from ase.units import Bohr, Hartree

# after
from ase.units import Bohr as _Bohr, Hartree as _Hartree
Bohr = float(_Bohr)
Hartree = float(_Hartree)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0135d16fbdea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.