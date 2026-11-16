# Issue

**Title:** ADD _ngl_focused

## Description

The aim is to implement camera synchronization. 
Without checking which view is focused, we introduce ping pong effect that cause the views shaking.
There's still work to do (e.g: cameras are still since it requires round trip frontend to backend).
(Can we we `jslink`?)

![camera](https://user-images.githubusercontent.com/4451957/59554937-ff162680-8f78-11e9-9a51-70c921bb1419.gif)

Code

```python
from itertools import combinations
```


```python
from IPython.display import display
import nglview as nv
from ipywidgets import *
from functools import partial
```


```python
def sync_camera(v0, v1):
    def on_camera(change):
        new = change['new']
        old = change['old']
        owner = change['owner']
        if new != old:
            if owner == v0 and v0._ngl_focused:
                v1._set_camera_orientation(new)
            elif owner == v1 and v1._ngl_focused:
                v0._set_camera_orientation(new)

    v0.observe(on_camera, ['_camera_orientation'])
    v1.observe(on_camera, ['_camera_orientation'])
```


```python
views = []
for _ in range(6):
    v = nv.show_file(nv.datafiles.ALA3)
    views.append(v)

for (v0, v1) in combinations(views, 2):
    sync_camera(v0, v1)
    
g = GridBox(views, 
            layout=Layout(
                grid_template_rows='auto auto auto',
                grid_template_columns='auto auto auto',
                grid_gap = '0px 0px'
            ))
g
```


    GridBox(children=(NGLWidget(), NGLWidget(), NGLWidget(), NGLWidget(), NGLWidget(), NGLWidget()), layout=Layout…



```python
for v in views:
    v.background = 'white'
    v.layout.width = '350px'
    v.layout.height = '300px'
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8a81ee25c07d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.