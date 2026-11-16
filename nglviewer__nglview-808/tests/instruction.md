# Issue

**Title:** We can call `render_image` multiple times within a cell now, no threading, no wait.

## Description

<img width="391" alt="Screen Shot 2019-05-22 at 1 22 05 AM" src="https://user-images.githubusercontent.com/4451957/58149305-5520d400-7c30-11e9-8650-abc1b2084a77.png">

Code
```
import nglview as nv
import threading
import time
from ipywidgets import Widget
import pytraj as pt
from nglview.contrib.movie import MovieMaker

v = nv.demo()
v

v.clear()
v.add_rope()
s0 = v.render_image()
v.clear()
v.add_cartoon()
s1 = v.render_image()

s0

s1
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad564cea9a31`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.