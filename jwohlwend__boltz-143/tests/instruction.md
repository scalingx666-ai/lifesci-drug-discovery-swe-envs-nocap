# Issue

**Title:** raise error when atom name encoding is violating the expected dimension

## Description

In this PR, we are aiming at raising an Error when an invalid atom name is generated from the given smiles.

When a larger molecule (this [example](https://pubchem.ncbi.nlm.nih.gov/compound/10078395)) is feed into boltz, we encountered a `SI101` atom name where it violates what we [expected](https://github.com/jwohlwend/boltz/blob/e3b5e1da6c9e3954ab4e3fb92563707c8961d3af/src/boltz/data/parse/schema.py#L100) (4-char string) in `convert_atom_name`. test code:

```
from rdkit import Chem
from rdkit.Chem import AllChem

seq = "CC(C)[C@@H](C(=O)C1=NC2=C(O1)C=CC(=C2)CO[Si](C)(C)C(C)(C)C)NC(=O)[C@@H]3CCCN3C(=O)[C@H](C(C)C)NC(=O)OCC4=CC=CC=C4"
mol = AllChem.MolFromSmiles(seq)
mol = AllChem.AddHs(mol)

# Set atom names
canonical_order = AllChem.CanonicalRankAtoms(mol)
for atom, can_idx in zip(mol.GetAtoms(), canonical_order):
    name = atom.GetSymbol().upper() + str(can_idx + 1)
    if len(name) > 4:
        print(name)
    atom.SetProp("name", name)
```

The above molecule gives a `SI101`, and `convert_atom_name` returns a `(51, 41, 17, 16, 17)` which later [numpy](https://github.com/jwohlwend/boltz/blob/e3b5e1da6c9e3954ab4e3fb92563707c8961d3af/src/boltz/data/parse/schema.py#L825) complains not being in the correct dimension.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e3b5e1da6c9e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.