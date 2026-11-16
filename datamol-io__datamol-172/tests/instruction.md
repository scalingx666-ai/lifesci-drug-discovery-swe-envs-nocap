# Issue

**Title:** Updated logging for _sanifix4.py

## Description

Checklist:

- [ ] Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate).
- [ ] Update the API documentation is a new function is added or an existing one is deleted.
- [X] Added a `news` entry.
  - _copy `news/TEMPLATE.rst` to `news/my-feature-or-branch.rst`) and edit it._

---

I noticed that in rare occasions, sanitizing a molecule could fail due to seemingly outdated usage of the logging module in `_sanifix4.py`. I propose to use the RDKit logger instead, because to me personally this code logically falls under RDKit and so that verbosity can be controlled through Datamol's `dm.without_rdkit_log()` context manager. 

Example in which logging could go wrong: 
```python
import datamol as dm
import numpy as np
import autosklearn.regression

smi = '[NH4][Pt]([NH4])(Cl)Cl'
mol = dm.to_mol(smi, ordered=True, sanitize=False)
mol = dm.sanitize_mol(mol)  # This will throw the normal warnings as expected

X = np.random.random((100, 10))
y = np.random.random((100, 1))

# AutoML configures the logging module
obj = autosklearn.regression.AutoSklearnRegressor(time_left_for_this_task=30)
obj.fit(X, y)

mol = dm.to_mol(smi, ordered=True, sanitize=False)
mol = dm.sanitize_mol(mol)  # This will now throw a logging error
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bc619e1fdb57`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.