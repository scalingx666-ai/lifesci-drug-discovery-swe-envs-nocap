# Issue

**Title:** ADD Custom color scheme API

## Description

A live version here: https://nbviewer.jupyter.org/github/arose/nglview/blob/644fa66a8461b52c01a5e4df4d2a99486b690fea/notebooks/custom_color.ipynb
(might need to Zoom Out to see the full page: #840 )

<img width="1201" alt="Screen Shot 2019-08-01 at 11 56 39 PM" src="https://user-images.githubusercontent.com/4451957/62343246-073e0d00-b4b8-11e9-9d96-6630c054848e.png">

Code

# Selection Scheme


```python
import nglview as nv
from nglview.color import ColormakerRegistry

cm = ColormakerRegistry
cm.add_selection_scheme("awesome",
        [['blue', '1-10']])
```


    _ColormakerRegistry()



```python
v0 = nv.demo(default=False)
v0.center()
v0.add_cartoon(color='awesome')
v0
```


    NGLWidget()



```python
assert v0._ngl_repr_dict['0']['0']['params']['colorScheme'] == 'awesome'
```

# Function


```python
cm.add_scheme_func('bla_bla','''
 this.atomColor = function (atom) {
     if (atom.serial < 1000) {
       return 0x0000FF // blue
     } else if (atom.serial > 2000) {
       return 0xFF0000 // red
     } else {
       return 0x00FF00 // green
     }
 }
''')
```


```python
v1 = nv.demo(default=False)
v1.center()
v1.add_cartoon(color='bla_bla')
v1
```


    NGLWidget()



```python
# nv.write_html('index.html', [v0, v1])

# !open index.html
# !google-chrome index.html

# NOTE: If using master branch, make sure to copy nglview/static/index.js to <this folder>/nglview-js-widgets.js
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bdf58b41fcc9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.