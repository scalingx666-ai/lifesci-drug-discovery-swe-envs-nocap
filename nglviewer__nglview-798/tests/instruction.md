# Issue

**Title:** ADD: show_prody

## Description

```python
    >>> import nglview as nv # doctest: +SKIP
    ... import prody
    ... structure = prody.parsePDB('what.pdb')
    ... ensemble = prody.parseDCD('what.dcd')
    ... ensemble.setAtoms(structure)
    ... nv.show_prody(ensemble)
    ... # nv.show_prody(structure)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9ae5ffdb7947`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.