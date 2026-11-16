# Issue

**Title:** Support color by volume

## Description

![color](https://user-images.githubusercontent.com/4451957/57813945-f1823c80-773f-11e9-8482-5cc92909da85.png)

Example:
(Data: https://github.com/arose/ngl/tree/master/data)

```python
import nglview as nv
```


```python
v = nv.NGLWidget()
v
```


    A Jupyter Widget



```python
c0 = v.add_component('esp.mol')
c1 = v.add_component('esp.dx')
```


```python
c0.clear()
c0.add_surface(color_scheme='volume', color_volume=c1,
      colorScale=[ 0xff0000, 0xffff00, 0x00ff00, 0x00ffff, 0x0000ff ],
      colorMode='rgb',
      colorDomain=[ -0.05, 0.05 ],
      opacity=0.5
)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f45da9c8e1d6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.