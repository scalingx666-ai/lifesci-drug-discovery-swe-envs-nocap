# Issue

**Title:** NGLWidget.add_component now tries to convert suitable objects

## Description

I've got a list of `rdkit.Mol`s I want to show, so currently I would have to do something like:

```python
for mol in mols:
    s = nv.RDKitStructure(mol)
    v.add_component(s)
```

This patch makes it so that `NGLWidget.add_component` will try and use the `BACKENDS` register to figure out foreign objects

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c886919ea966`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.