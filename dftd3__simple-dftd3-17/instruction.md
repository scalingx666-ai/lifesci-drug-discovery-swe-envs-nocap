# Issue

**Title:** Support PySCF

## Description

Supply an interface like [pyscf/dftd3](https://github.com/pyscf/dftd3).

- [x] cleanup implementation (handle incorrect damping versions, ...)
- [x] add type hints for function signatures
- [x] add examples to docstrings
- [x] document in README / sphinx pages

Related

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4a95d4e66e1a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.