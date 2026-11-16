# Issue

**Title:** activate extension

## Description

#896 

```
$ jupyter-nbextension  list
Known nbextensions:
  config dir: /Users/haichit/miniconda3/etc/jupyter/nbconfig
    notebook section
       ...
      nglview-js-widgets/extension  enabled 
      ...
```

PS: only works with `pip install`, not `python setup.py install`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e181b16a762e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.