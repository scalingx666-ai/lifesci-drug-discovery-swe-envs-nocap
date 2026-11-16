# Issue

**Title:** Improve handling of custom force field

## Description

Here all custom force fields are added to a directory to prepare the protein and the membrane. The path of the directory is passed to `MakeInput` class with `custom_ff_path`. Then, include statements of the type `include "charmm36-jul2022.ff/forcefield.itp"` are allowed for topology files. In addition, the user can now from the definition of the protein or the memebrane just specify the code like

```python
protein = {
  'conf': 'protein.pdb',
  'ff': {
    'code': 'user_force_field_code'
  }

}
```
Basically, what is done is:

```python
os.environ["GMXLIB"] = os.path.abspath(custom_ff_path)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a9bd6bd56055`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.