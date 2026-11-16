# Issue

**Title:** Reload charge etc from file

## Description

##  

```python
>>> from autode import Molecule
>>> mol = Molecule(smiles="[O+]", mult=2, charge=1, solvent_name="water")
>>> mol.print_xyz_file(filename="tmp.xyz")
>>> Molecule("tmp.xyz")
Molecule(tmp, n_atoms=1, charge=1, mult=2)
```

***

## Checklist

* [x] The changes include an associated explanation of how/why
* [x] Test pass
* [x] Documentation has been updated
* [x] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d29a528134ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.