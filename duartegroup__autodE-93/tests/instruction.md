# Issue

**Title:** Improves calc_thermo usability

## Description

This PR improves (makes more intuitive) the behaviour of `species.calc_thermo()` by: (1) Running a calculation if the function is called with one and (2) Allows for keywords to be directly specified. The latter improves consistency between calc_thermo and `optimise` / `single_point` methods, each of which generate and run a QM calculation. Thanks to @asterlingchem for the suggestions!

For example, it enables:

```python
import autode as ade

water = ade.Molecule(smiles='O')
water.calc_thermo(keywords=ade.HessianKeywords(['PBE', 'def2-SVP', 'Freq']),
                  method=ade.methods.ORCA())
```

This PR also adds a `zpe` property of a species, containing its zero point energy

```
>>> import autode as ade
>>> water = ade.Molecule(smiles='O')
>>> water.zpe is None
autode.log.log: WARNING  No Hessian has been calculated - no frequencies
autode.log.log: WARNING  Vibrational frequencies not available, cannot determine zero point energy
True
>>> water.calc_thermo()
...
>>> water.zpe.to('kcal mol-1')
Energy(12.25045 kcal mol-1)
```


***

- [x] Improve usability of calc_thermo
- [x] Add documentation example
- [x] Add `zpe` property to a species

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `56fd4c78e7d7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.