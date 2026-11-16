# Issue

**Title:** Ngl 0.10.5-17

## Description

Also

- `add_component` will return a `ComponentViewer` object
```python
c = view.add_component(...)
c.add_cartoon(...)
view.remove_component(c)
```
- add `_call` for ComponentViewer
```
c._call("setPosition", [1, 2, 3])
```
- Deperacated `center_view` in favor of `center`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bff6b08ce28f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.