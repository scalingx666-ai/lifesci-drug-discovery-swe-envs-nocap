# Issue

**Title:** Fix CI for RDKit and Windows

## Description

This PR pins RDKit on Windows to `rdkit<=2024.03.4`.




Additionally, unused `rustworkx`-only conda environments are removed.

---

CI for Windows [started failing](https://github.com/RMeli/spyrmsd/actions/runs/10086122312), while Linux is not affected. macOS is too slow to complete before jobs are cancelled, but locally everything works fine.

The error is the following:
```
ERROR tests/test_rmsd.py::test_rmsdwrapper_single_molecule[networkx-lambda_max_fast-minimize] - NameError: name 'load' is not defined
ERROR tests/test_rmsd.py::test_rmsdwrapper_single_molecule[networkx-lambda_max_fast-no_minimize] - NameError: name 'load' is not defined
ERROR tests/test_rmsd.py::test_rmsdwrapper_single_molecule[networkx-lambda_max_fallback-minimize] - NameError: name 'load' is not defined
ERROR tests/test_rmsd.py::test_rmsdwrapper_single_molecule[networkx-lambda_max_fallback-no_minimize] - NameError: name 'load' is not defined
===== 44 failed, 128 passed, 34 skipped, 4 warnings, 706 errors in 15.67s =====
```
and seems to appear only on Windows (and possibly only with RDKit).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `29e1fd618e06`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.