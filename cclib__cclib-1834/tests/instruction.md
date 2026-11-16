# Issue

**Title:** Add initial pixi support

## Description

Try it with
```bash
pixi run -e py38 -x python -m pytest -n 8 --dist worksteal -k 'not pyscf'
# Psi4 not available for Python 3.14 yet
pixi run -e py314 -x python -m pytest -n 8 --dist worksteal -k '(not pyscf) and (not psi4)'
```

I've confirmed locally that all 6 Python versions are working.  The lockfile solve time is annoying since it's the Cartesian product of Python versions and platforms but :shrug:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2a6fd72d316d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.