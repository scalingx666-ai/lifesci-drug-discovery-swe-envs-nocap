# Issue

**Title:** bugfix: py_utils.get_name and widget.NGLwidget

## Description

Giving arbitrary names when adding component is now possible, before, these calls:

`iwd.add_component(nglview.FileStructure("test.pdb"),name="test")`
`comp = iwd.add_component(nglview.FileStructure("test.pdb"),{"name":"test"})`

resulted in nothing or error (see screenshot), because `kwargs` was being passed internally instead of `**kwargs`

@hainm, I hope it's okay I opened the PR directly, this one was driving me crazy since last week ;) 

![Screenshot_20210608_112955](https://user-images.githubusercontent.com/7518004/121160911-cac65f80-c84c-11eb-8344-61ffd07840fb.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `df70ba569562`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.