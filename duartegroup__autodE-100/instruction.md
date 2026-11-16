# Issue

**Title:** Keyword type inference

## Description

Improves usability when calling `single_point()` or `optimise()` on a `species` by infering the type of keywords needed to perform the calculation e.g.

```python
import autode as ade
mol = ade.Molecule(smiles='O')
mol.single_point(method=ade.methods.ORCA(), 
                 keywords=['SP', 'B3LYP', 'def2-SVP'])
```

also allows for keywords to be given as a string with

```python
mol.single_point(method=ade.methods.ORCA(), 
                 keywords='SP B3LYP def2-SVP')
```

***

- [x] Update changelog
- [x] Update documentation
- [x] Add tests

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72dc395a2fa5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.