# Issue

**Title:** Error handling for PaDEL-Descriptor not returning any calculated values

## Description

This update includes handling for an error observed in issue  where some compounds would return no computed descriptors/fingerprints (temporary CSV not saving an entry for the compound).

For example, the compound "buprenorphine" with SMILES string "Oc7ccc5c1c7O[C@H]3[C@]6(OC)C@HC@@(C)C(C)(C)C" would produce an output CSV file with no entry for the compound when the following is executed:
```python
from padelpy import from_smiles

from_smiles('Oc7ccc5c1c7O[C@H]3[C@]6(OC)C@HC@@(C)C(C)(C)C', output_csv='output.csv')
```

When PaDELPy re-imports these descriptors to return to the user, an indexing error occurred due to the _from\_smiles_ function (and the _from\_mdl_ function, it has the same behavior) looking through an empty list.

This update ensures that the following exception is raised if this behavior occurs:
```
RuntimeError: PaDEL-Descriptor returned no calculated values. Ensure the input structure is correct.
```

One of buprenorphine's alternate SMILES strings, "C[C@([C@H]1C[C@@]23CC[C@@]1([C@H]4[C@@]25CCN([C@@h]3CC6=C5C(=C(C=C6)O)O4)CC7CC7)OC)(C(C)(C)C)O", also produces this error. Another alternate SMILES string, "CC(C)(C)C(C)(C1CC23CCC1(C4C25CCN(C3CC6=C5C(=C(C=C6)O)O4)CC7CC7)OC)O", simply causes a timeout error (unable to calculate descriptors given 60 minutes of available runtime, as stated in the above issue). 

The issue cited above states that the GUI version of PaDEL-Descriptor is also unable to calculate values for these SMILES, therefore I theorize that the underlying issue is likely within PaDEL-Descriptor.

This update also includes updated DocStrings.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `99eabb5130de`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.