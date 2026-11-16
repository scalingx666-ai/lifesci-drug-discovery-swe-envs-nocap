# Issue

**Title:** docs for shape and move some methods to private

## Description

```bash
view.shape.add_cone?

Signature: view.shape.add_cone(*args)
Docstring:
# add_cone(position1, position2, color, radius, name) 
>>> shape.add_cone( [ 0, 2, 7 ], [ 0, 3, 3 ], [ 1, 1, 0 ], 1.5 )
File:      ~/programs/3d/nglview/nglview/shape.py
Type:      method
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8fee413ad7f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.