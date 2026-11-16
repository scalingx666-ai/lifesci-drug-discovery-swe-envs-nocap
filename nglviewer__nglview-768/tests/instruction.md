# Issue

**Title:** add execute_code

## Description

Aim:
- Quickly test new idea without recompile js code
- JS user can play around with NGL in python.

```python
code = """
var stage = this.stage;
var view = this.stage.viewer;
for (x in view){
    console.log(x)
}
"""

v._remote_call('execute_code', target='Widget', args=[code])

or using shortcut
v._execute_js_code(code)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8d3d948b00ba`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.