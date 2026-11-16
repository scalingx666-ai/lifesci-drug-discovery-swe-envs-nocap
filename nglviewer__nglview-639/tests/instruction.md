# Issue

**Title:** ENH: nightwatch (again)

## Description

Damn, finally I can make notebook test with `chromedriver` works again.
Very tricky (need to use correct `chromedriver` version (in this case, v2.30)). 

Example
---------
```
$ nightwatch 
Starting selenium server... started - PID:  17011

[Render Image] Test Suite
=============================

Running:  nglview/tests/notebooks/api/render_image.ipynb
url http://localhost:8889/notebooks/nglview/tests/notebooks/api/render_image.ipynb
 ✔ Passed [ok]: Check that python has no error
 ✔ Passed [ok]: Check that python has no error
 ✔ Passed [ok]: Check that python has no error
 ✔ Passed [ok]: Check that python has no error
 ✔ Passed [ok]: Check that python has no error
 ✔ Passed [ok]: Check that python has no error
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4d9045f11044`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.