# Issue

**Title:** Chemical groups

## Description

## Changelogs

-  Fix issues with protecting group by adding exact query match with terminal group filtering and using custom matches rather than catalog-derived match

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation is a new function is added, or an existing one is deleted._
- [ ] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---
The following now works as intended: 
```python
import medchem as mc
import datamol as dm

non_protected_smiles = ["C1=CC=C2C(=C1)C(=O)OC2(C3=CC=C(C=C3)O)C4=CC=C(C=C4)O", "CC(=CCCC(C)(C=C)OC(=O)C)C", "CCC1(C(=O)N(C(=O)O1)C)C", "CC1=CCC(CC1)C(C)(C)OC(=O)C", "CCC(=O)OC(C)(C)C1CCC(=CC1)C"]
protected_smiles = ["CC(C)(C)OC(=O)N1CCC(CC1)N", "CC(C)(C)OC(=O)NCC(=O)O", "CC(C)(C)OC(=O)N1CCCC1C(=O)O", "CC(C)(C)OC(=O)NC(COCC1=CC=CC=C1)C(=O)O", "CC(=O)OC(C)(C)C"]

non_protected_mols = [dm.to_mol(x) for x in non_protected_smiles]
protected_mols = [dm.to_mol(x) for x in protected_smiles]

# Apply the filter
out = mc.functional.protecting_groups_filter(
    non_protected_mols + protected_mols,
    protecting_groups=[
        "fmoc",
        "tert-butoxymethyl",
        "tert-butyl carbamate",
        "tert-butyloxycarbonyl",
    ],
    n_jobs=-1,
    progress=True,
    return_idx=False,
)

legends = [f"Pass the filter={o}" for o in out]
dm.to_image(non_protected_mols + protected_mols, legends=legends, n_cols=5, mol_size=(250, 150), use_svg=False)

```
![image](https://github.com/datamol-io/medchem/assets/5290110/2f98f57c-f258-43ec-8ce4-79fff18e9d1c)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `45bd4f6e1d1a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.