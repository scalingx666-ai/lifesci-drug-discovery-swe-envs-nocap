# Issue

**Title:** View a Biopython object

## Description

I thought a cool idea would be that you could view a Biopython structural object in Jupyter using nglview.

I have put together some code that lets you do the following:

```python
import nglview as nv
from Bio.PDB import PDBParser

# Read in a PDB file with Biopython
parser = PDBParser()
structure = parser.get_structure("1AKE", "1AKE.pdb")

# Show a structure
view1 = nv.show_biopython(structure)
view1

# Show a chain
view2 = nv.show_biopython(structure[0]["A"])
view2

# Show a residue
view3 = nv.show_biopython(structure[0]["A"][50])
view3
```

It writes the Biopython object out to a string and reads that back in with `show_text`.

Let me know what you think. Current problems are that you need the old `StringIO` method because Biopython writes strings not unicode, and that the Bio.PDB.PDBIO import is required.

CC @sbliven.

Screengrab here:
<img width="738" alt="screen shot 2017-07-20 at 17 00 33" src="https://user-images.githubusercontent.com/6620652/28424208-51d55452-6d6d-11e7-9716-233d5b85c074.png">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `728ca960cfb4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.