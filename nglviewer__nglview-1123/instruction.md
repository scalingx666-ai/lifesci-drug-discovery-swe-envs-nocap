# Issue

**Title:** Remove upper boundary from jupyter_packaging version

## Description

Hey,
currently nglview is not installable under Python 3.13.
The reason is a deprecation concerning the jupyter_packaging build packaging dependency: 
Simply unbounding the dependency allows the installation under 3.13 (installation tested in a Docker container, but maybe one should check if everything still works correctly).
For 3.13 we need a version of at least 0.12.2, but I opted to not set `jupyter_packaging>=0.12.2` since 0.12.2 does only support Python 3.7+, while nglview supports Python 3.6+.
It would be cool if we could get a new version on PyPI to make the package installable again :)
Best,
Wanja

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65104788af3a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.