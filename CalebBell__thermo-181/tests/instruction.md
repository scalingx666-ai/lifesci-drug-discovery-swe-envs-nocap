# Issue

**Title:** Assume `f_der` methods can be tuples

## Description

@CalebBell,

I ran into this bug with extrapolating the viscosity of a chemical. The issue comes from the `TDependentProperty` object assuming that all `f_der` methods return floats. For the special case of  `chemicals.viscosity.dPPDS9_dT`, it returns a tuple with the first value being the derivative, the second being the actual viscosity. 

You can reproduce the error as follows:

```python
from thermo import Chemical
chemical = Chemical('2-methylnaphthalene')
chemical.ViscosityLiquid(300, 0.2 * 101325)
chemical.ViscosityLiquid.RAISE_PROPERTY_CALCULATION_ERROR = True
chemical.ViscosityLiquid.TP_dependent_property(300, 0.2 * 101325)
```
```
RuntimeError: Failed to evaluate liquid viscosity method 'LUCAS' at T=300 K and P=20265.0 Pa for component with CASRN '91-57-6'
```

In this pull request, I added additional logic to accommodate this special case with tuples. Then the return value is `0.0021504854722795615`.

If you approve of this change, I can go ahead and add this case as a test.

Thanks!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `57dd6ce8f250`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.