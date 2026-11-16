# Issue

**Title:** Improve Molecule constructor

## Description

Currently a `Molecule` initialised from a .xyz filename cannot also have a name specified. For example 

```python
>>> import autode as ade
>>> mol = ade.Molecule('water.xyz', name='h2o')
Traceback (most recent call last):
 File "<stdin>", line 1, in <module>
TypeError: __init__() got multiple values for argument 'name'
```

this PR fixes this and maintains the signature, i.e.:

```python
>>> mol = ade.Molecule('water.xyz', name='h2o')
>>> mol.name
'h2o'
>>> 
>>> mol = ade.Molecule('water.xyz')
>>> mol.name
'water'
```

***
### TODO

- [x] Test

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58c62a0647a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.