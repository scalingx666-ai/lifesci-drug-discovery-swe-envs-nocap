# Issue

**Title:** ADD: perframe_hook for MovieMaker

## Description

Close #620 

CODE:
```python
import pytraj as pt
import nglview as nv
from nglview.contrib.movie import MovieMaker

traj = pt.datafiles.load_trpcage()[:4]
view = nv.show_pytraj(traj)
view
```


```python
def update_color(view):
    if view.frame % 2 == 0:
        view.update_cartoon(color='red')
    else:
        view.update_cartoon(color='blue')
```


```python
MovieMaker(view, in_memory=True, perframe_hook=update_color).make()
```


```python
from IPython.display import Image
```


```python
Image(filename='./my_movie.gif')
```

Effect:
![my_movie](https://user-images.githubusercontent.com/4451957/58071902-0f023c80-7b6c-11e9-93ba-d3804d122a76.gif)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f726dc22f27c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.