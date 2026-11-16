# Issue

**Title:** fix: handle missing results from lilly-demerits

## Description

## Changelogs
- Handle molecules dropped by `lilly-demerits`, avoiding the row-count mismatch that previously triggered the ValueError. (#23)

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] _Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation is a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, **`fix`** or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_
#23 : @maclandrol mentioned that, marking these results as invalid SMILES would make sense so user would know what happens makes sense. While I agree with the idea, I am not entirely sure what the result should look like. 

Currently, the results for missing entry is hand-crafted, as:
```py
{
  "smiles": dm.to_smiles(dm.to_mol(mols[i])),
  "ID": i,
  "reasons": "lillymol_invalid",
  "step": 0,
  "demerit_score": np.nan,
  "status": "Exclude",
  "pass_filter": False,
  "mol": mols[i],
}
```
So that the result looks consistent with other failures. However, I am wondering whether marking it as step-0 failure is a correct way. Any suggestions / fixes on this would be great!

By this PR, SMILES list supplied in #23 (@anna-vasileva-insilico) returns in dataframe with 119 rows (the length of original SMILES list), with 47th row (the problematic smiles) correctly handled.  

The result of 
```
smiles_list = [
    'O=[N+]([O-])c1ccc(C=C=c2cc3scnc4snc([nH]2)c4-3)cc1',
    'C=C=c1c2c3c(cc1n1c4c(c(=O)n(C)c21)C(N1CCC(O)(C(=O)O)CC1)c1ccccc1CC4)=C=CCN=3',
    'COC(=O)c1cc2c(O)c(C(=O)OC)c(=C3CNc4ccccc43)[n+](=C=Cc3ccccc3)c2s1',
    'CCC'
]
``` 
by @GurevichPE in #23 looks like this 
```
                                              smiles               reasons  step  demerit_score   status  pass_filter                                                mol
0  O=[N+]([O-])c1ccc(C=C=c2cc3scnc4snc([nH]2)c4-3...      lillymol_invalid     0            NaN  Exclude        False  O=[N+]([O-])c1ccc(C=C=c2cc3scnc4snc([nH]2)c4-3...
1  C=C=c1c2c3c(cc1n1c4c(c(=O)n(C)c21)C(N1CCC(O)(C...      lillymol_invalid     0            NaN  Exclude        False  C=C=c1c2c3c(cc1n1c4c(c(=O)n(C)c21)C(N1CCC(O)(C...
2  COC(=O)c1cc2c(O)c(C(=O)OC)c(=C3CNc4ccccc43)[n+...      lillymol_invalid     0            NaN  Exclude        False  COC(=O)c1cc2c(O)c(C(=O)OC)c(=C3CNc4ccccc43)[n+...
3                                                CCC  no_interesting_atoms     1            NaN  exclude        False                                                CCC
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ccf5d76a89fa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.