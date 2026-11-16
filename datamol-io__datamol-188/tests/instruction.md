# Issue

**Title:** fuzzy_scaffold can now return a pandas dataframe that is more readable.

## Description

Hello!  This is for issue #114.  So this edit is quite opinionated. I don't know if you guys would this kind of organized dataframe. But first I have to discuss where I added this change. I decided to add a optional flag for datamol users in the `fuzzy_scaffolding` function. <strike>The flag is termed `if_df`, which is defaulted to `False`. </strike> The flag is termed `if_df`, which is defaulted to `True`.  **Two** separate pandas dataframe for each `scf2infos` and `scf2groups` will be returned. The rationale is not to confuse users on how `fuzzy_scaffolding` function would return previously.

NOTE: the output below is my best attempt to express the pandas dataframe. The output is just a df that has `3` columns and not `15` rows.

### Let's start with `scf2infos`

The way scf2infos is structured is absolutely perfect to be pandas transposed. Every scaffold output has its corresponding rdkit `mol` list and its `smarts` pattern. This means every row will represent the `scf` and every `scf` will have its `mol` list.

output:
```
                                         scf  \
index                                          
0                      CC(CC1CCCCC1)CC1CCCC1   
1                     CC(CCC1CCCCC1)CC1CCCC1   
2                    CC(CCCC1CCCC1)CCC1CCCC1   
3                      CC(CC1CCCCC1)C1CCCCC1   
4      CC(CCC1CCC(C2CCC3CCCCC32)C1)CC1CCCCC1   

                                                    mols  \
index                                                      
0        [<rdkit.Chem.rdchem.Mol object at 0x1108a1a80>]   
1      [<rdkit.Chem.rdchem.Mol object at 0x1108a06d0>...   
2        [<rdkit.Chem.rdchem.Mol object at 0x1108a0200>]   
3        [<rdkit.Chem.rdchem.Mol object at 0x1108a2dc0>]   
4        [<rdkit.Chem.rdchem.Mol object at 0x1108a2c00>]   

                                                  smarts  
index                                                     
0      [#6]1:&@[#6]:&@[#6]:&@...  
1      [#6]-&!@[#8]-&!@[#6]1:&@[#6]:&@[#6]:&@-&!@[#6]-&!@[#1...  
3      [#6]1-&@[#6]-&@[#6]-&@[#6]-&@[#6]-&@[#7]-&@1-&...  
4      (-&!@[#8]-&!@[#6]-&!@[#6]1...  
```



### What about `scf2groups`?

scf2groups is trickier because the core 'groups' are in their individual dictionaries contained in a list. This can be difficult to create a df due to these multi-valued attributes. Thankfully, Pandas can control for the multi-valued attributes by calling from the `.from_dict()` method and setting `orient` to `'index'`. Further, this allows the df for each `scf` row to have `None` values if there are no results. So this df will dynamically create `n_core_group`s if there is an output with `n` number of core groups. So in the case below, `scf` index `1` has two core groups but the rest do not. 

```
                                         scf  \
index                                          
0                      CC(CC1CCCCC1)CC1CCCC1   
1                     CC(CCC1CCCCC1)CC1CCCC1   
2                    CC(CCCC1CCCC1)CCC1CCCC1   
3                      CC(CC1CCCCC1)C1CCCCC1   
4      CC(CCC1CCC(C2CCC3CCCCC32)C1)CC1CCCCC1   

                                            0_core_group  \
index                                                      
0      {'Core': <rdkit.Chem.rdchem.Mol object at 0x11...   
1      {'Core': <rdkit.Chem.rdchem.Mol object at 0x11...   
2      {'Core': <rdkit.Chem.rdchem.Mol object at 0x11...   
3      {'Core': <rdkit.Chem.rdchem.Mol object at 0x11...   
4      {'Core': <rdkit.Chem.rdchem.Mol object at 0x11...   

                                            1_core_group  
index                                                     
0                                                   None  
1      {'Core': <rdkit.Chem.rdchem.Mol object at 0x11...  
2                                                   None  
3                                                   None  
4                                                   None  
```

Other than that. I hope you like the code. I also updated the test cases. 

Thanks, 
Steven Pak

Checklist:

- [x] Was this PR discussed in a issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR. 
- [x] Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate).
- [ ] Update the API documentation is a new function is added or an existing one is deleted.
- [x] Added a `news` entry.
  - _copy `news/TEMPLATE.rst` to `news/my-feature-or-branch.rst`) and edit it._

---

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9bb62587e704`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.