# Issue

**Title:** ADD: _view_xz_plane

## Description

hidden for now
```
view = nglview.show_structure_file('./rho.pdb')
view.control._view_xz_plane()
view
```

from: 

close #511

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b873831de1e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.