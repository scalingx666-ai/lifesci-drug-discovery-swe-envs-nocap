# Issue

**Title:** Fix setup to install Sella successfully through pip

## Description

Currently (`Sella-2.0.1.`), the automatic installer will fail if there is no `numpy` or `cython` installed on your system. Even if you preinstall those two packages, the `pip install sella` command returns a number of errors of these type:

```bash
    sella/force_match.c:606:10: fatal error: 'numpy/arrayobject.h' file not found
    #include "numpy/arrayobject.h"
             ^~~~~~~~~~~~~~~~~~~~~
    1 error generated.
    error: command '/usr/bin/clang' failed with exit code 1
```

With this PR, the setup is fixed by adding `pyproject.toml` file holding information about software required by `Sella` to be properly compiled and installed. Now, once you type:

```bash
pip install .
```
`Sella` installs and works nicely.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58c5c2378ced`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.