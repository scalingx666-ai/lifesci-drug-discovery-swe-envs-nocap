# Issue

**Title:** 0.10.0-dev.8 + adding ViewerControl

## Description

#596 

EXPERIMENTAL

Dummy example:

```python
    view = nv.demo()
    view

    mat = [11, 12, 13, 14,
           21, 22, 23, 24,
           31, 32, 33, 34,
           41, 42, 43, 44]
 
    vector = [0, 1, 2]

    view.control.align(mat)
    view.control.rotate(mat)
    view.control.translate(vector)
    view.control.apply_matrix(mat)
    view.control.center(vector)
    view.control.orient(mat)
    view.control.zoom(0.3)
    view.control.rotate(mat)
    view.control.spin(vector, 0.1)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72f39f5873a3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.