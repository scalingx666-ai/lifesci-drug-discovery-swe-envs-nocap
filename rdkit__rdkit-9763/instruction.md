# Issue

**Title:** Do not use non-structural information in stereoisomer deduplication

## Description

Currently, the C++ Stereoisomer Enumerator uses CXSMILES with no coordinates to deduplicate stereoisomers. This leads to some cases in which stereoisomers are not correctly deduplicated due to non-structural information, e.g.:
```python3
In [3]: from rdkit import Chem
   ...: from rdkit.Chem import rdEnumerateStereoisomers
   ...:
   ...: def do_enumerate(mol, label):
   ...:    enum = rdEnumerateStereoisomers.StereoisomerEnumerator(m)
   ...:
   ...:    while True:
   ...:       isomer = enum.next()
   ...:       if isomer is None:
   ...:          break
   ...:       print(label, Chem.MolToSmiles(isomer))
   ...:    print('')
   ...:
   ...:
   ...: Chem.SetUseLegacyStereoPerception(False)
   ...:
   ...: m = Chem.MolFromSmiles('FC1CC2CCC(C1)C2')
   ...:
   ...: do_enumerate(m, 'No props: ')
   ...:
   ...: for i, at in enumerate(m.GetAtoms()):
   ...:     at.SetProp('mapped_idx', str(i))
   ...:
   ...: do_enumerate(m, 'Maped indexes: ')

No props:  F[C@H]1C[C@@H]2CC[C@@H](C1)C2
No props:  F[C@@H]1C[C@H]2CC[C@@H](C1)C2
No props:  F[C@H]1C[C@H]2CC[C@H](C1)C2
No props:  F[C@H]1C[C@H]2CC[C@@H](C1)C2

Maped indexes:  F[C@H]1C[C@@H]2CC[C@@H](C1)C2
Maped indexes:  F[C@H]1C[C@H]2CC[C@H](C1)C2
Maped indexes:  F[C@@H]1C[C@H]2CC[C@@H](C1)C2
Maped indexes:  F[C@H]1C[C@H]2CC[C@@H](C1)C2
Maped indexes:  F[C@H]1C[C@H]2CC[C@H](C1)C2
Maped indexes:  F[C@H]1C[C@H]2CC[C@@H](C1)C2
Maped indexes:  F[C@H]1C[C@@H]2CC[C@@H](C1)C2
Maped indexes:  F[C@@H]1C[C@H]2CC[C@@H](C1)C2
```

This happens because even if the information is the same, the order in which it is written in the CX string makes the deduplication check fail.

This PR removes non-structural information from the deduplication CXSMILES generation.

I suspect we might need to dig deeper and just use SMLES (no CX) for the deduplication, as we do in the pure Python stereoisomer enumerator, but that seems to currently break atropisomer enumeration. So, for now, I'll go with removing just the non-structural information, until I can find some more time to dig into how atropisomer enumeration works.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `78cb05c3db00`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.