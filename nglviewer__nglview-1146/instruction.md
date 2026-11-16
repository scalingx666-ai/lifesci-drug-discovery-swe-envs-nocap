# Issue

**Title:** Try molstar

## Description

- https://molstar.org/
- I am having another package here https://github.com/hainm/molstarview but it duplicates lots of code from `nglview`. 
- So this is the PR for including molstar in nglview. It's weird but it saves my time. 
- Have to use `npx sass node_modules/molstar/lib/mol-plugin-ui/skin/light.scss > src/light.css` ()

```python
# cell1
import nglview as nv
from nglview.widget_molstar import MolstarView
view = MolstarView()
view

# cell 2
st = nv.FileStructure(nv.datafiles.PDB)
view.add_structure(st)
```

<img width="997" alt="image" src="https://github.com/user-attachments/assets/bedb1586-a621-4990-abd4-58c3a8f4102c">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `83802f68f509`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.