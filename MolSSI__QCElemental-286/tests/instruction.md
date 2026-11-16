# Issue

**Title:** fix circular import in docs

## Description

## Description
- [x] Sphinx warns about can't import `ProtoModel` when documenting (with autodoc and typing utilities) `qcel.testing.compare_recursive`. Can't be evaded by import guards b/c Sphinx uses runtime. This works around it and will be for Psi4 docs.
- [x] Fixes some `git+git` to `git+https` since GH doesn't authenticate the former anymore.
- [x] Removes some pytest>=4 restrictions now that pytest has reached 7
- [x] linted
- [x] test py310 and try to remove double testing for branches on upstream

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cabec4a7d109`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.