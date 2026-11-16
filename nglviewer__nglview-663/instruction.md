# Issue

**Title:** FIX add_shape, make sure it works if display view 2nd time.

## Description

I have no idea why but adding "time.sleep" before sending addShape request to NGL will help.

@arose Is there any special thing about Shape that causes the issue? How ShapeRepresentation is different from others?

Please have a look at implementation here:  https://github.com/arose/nglview/blob/master/js/src/widget_ngl.js#L524-L550

FIXED:
![add_shape](https://user-images.githubusercontent.com/4451957/29000355-988e190e-7a35-11e7-8097-fdf589a4611d.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `942904b56922`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.