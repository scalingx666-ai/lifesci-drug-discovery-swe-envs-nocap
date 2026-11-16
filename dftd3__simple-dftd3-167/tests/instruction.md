# Issue

**Title:** Fix realspace_cutoff handling in ASE calculator

## Description

Addresses review feedback on PR #154 for the `realspace_cutoff` feature in the ASE calculator.

**Fixed docstring**
- Corrected unit conversion guidance: values in Bohr should be multiplied by `ase.units.Bohr`, not divided
- Aligned `realspace_cutoff` default to `{}` (was `None`) for consistency with `params_tweaks`

**Fixed cache_api=True behavior**
- Extracted `_apply_realspace_cutoff()` helper method that applies cutoffs to the dispersion model
- Called in `calculate()` before evaluation instead of only during model creation
- Enables `calc.set(realspace_cutoff=...)` to update cutoffs on cached calculators

**Added test coverage**
- `test_ase_realspace_cutoff()` validates custom cutoffs change results, dynamic updates via `set()` work with caching, and empty dict uses library defaults

```python
from dftd3.ase import DFTD3
from ase.build import molecule

atoms = molecule("H2O")
calc = DFTD3(method="PBE", damping="d3bj", cache_api=True)
atoms.calc = calc
energy1 = atoms.get_potential_energy()

# Update cutoffs dynamically - now works with cache_api=True
calc.set(realspace_cutoff={"disp2": 0.5, "disp3": 0.5, "cn": 0.5})
energy2 = atoms.get_potential_energy()  # Different result
```

<!-- START COPILOT CODING AGENT TIPS -->
---

✨ Let Copilot coding agent  — coding agent works faster and does higher quality work when set up for your repo.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a531b4be693a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.