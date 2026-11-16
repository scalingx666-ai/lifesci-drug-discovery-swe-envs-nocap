# Issue

**Title:** Fix error if max_replacements is too small

## Description

`mutate_mol` raises `StopIteration` error when `max_replacements` is smaller than number of replacement generated. It is better to return here rather than raising error.

```python
from rdkit import Chem
from crem.crem import mutate_mol

db_name = "replacements02_sc2.5.db"
print(
    [
        m
        for m in mutate_mol(
            Chem.MolFromSmiles("CCC(C)C(N)C(N)=O"),
            db_name=db_name,
            radius=3,
            min_inc=-2,
            max_inc=2,
            max_replacements=5,
        )
    ]
)
```
```
  File "crem.py", line 418, in mutate_mol
    for frag_sma, core_sma, freq, ids in __gen_replacements(mol1=mol, mol2=None, db_name=db_name, radius=radius,
RuntimeError: generator raised StopIteration
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca6da730c16f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.