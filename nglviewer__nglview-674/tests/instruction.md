# Issue

**Title:** add set_coordinates for ComponentViewer

## Description

I think this will make better API.
It will be helpful for real time visualization. Also make it possible to mouse interaction if need editing 
structure.

```
view = nv.show_structure_file(...)
view

c = view[0]
c.set_coordinates(arr)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f8875ba588d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.