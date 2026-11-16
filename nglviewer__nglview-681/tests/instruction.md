# Issue

**Title:** ADD support sphinx-jupyter

## Description

Thanks to Jason: 

Need this PR: 

### Original code
```python
.. ipywidgets-display::
    from ipywidgets import Text
    Text("hello")

.. ipywidgets-display::

    import nglview as nv
    from IPython import display

    view = nv.NGLWidget()
    view.add_pdbid("1kx5")
    view._set_serialization()
    display.display(view)
```

## What you see !!! 
<img width="1038" alt="screen shot 2017-08-18 at 1 09 10 am" src="https://user-images.githubusercontent.com/4451957/29445003-f0d16a28-83b1-11e7-95f7-dbfb67438aa3.png">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `84a5873d98a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.