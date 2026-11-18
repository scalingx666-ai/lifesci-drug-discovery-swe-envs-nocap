# Issue

**Title:** Fix package version issues (jupyterlab, pypdb, rdkit, black-nb)

## Description

## Description

Pin JLab 2 because JLab 3 is not compatible yet with `nglview` (details ) and fix problems with `pypdb` and `rdkit` uncovered by the CI along the way :)


## TODOs

- [x] Pin JLab using `jupyterlab=2` in 3 environment files :) -- OUTDATED
  - `devtools/conda-envs/test_env.yml`
  - `devtools/conda-envs/users_env.yml`
  - `environment.yml`
 - [x] Upgrade to JLab 3
- [x] CI shows `black-nb` error: "error: cannot format teachopencadd/talktorials/T002_compound_adme/talktorial.ipynb: INTERNAL ERROR: Black produced different code on the second pass of the formatter."
- [x] T002/T004/T006: `AttributeError: module 'pandas.io.formats.format' has no attribute '_get_adjustment'` (`rdkit`'s `PandasTools`), see 
- [ ] T008: `AttributeError: module 'pypdb' has no attribute 'make_query'`, `AttributeError: module 'pypdb' has no attribute 'get_ligands'`, check with 
- [ ] T009: Result from T008 fail? `EmptyDataError: No columns to parse from file`
- [ ] T010: Again `pypdb` problems
- [x] black-nb needs a new release on PyPI -- pending


## Questions

## Status

- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eec8eaed8175`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.